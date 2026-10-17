# Diccionario de datos

## 1. Metadatos

* **Fecha:** 17/10/2026
* **Versión:** 0.1
* **Autores:** Brenda Mirano
* **Custodio:** R-PRO

## 2. Propósito

Este diccionario es la única fuente de definiciones de campos del proyecto. Las fichas de entidad, el catálogo sintético y los casos de prueba usan estos nombres. No diseña tablas ni garantiza campos nativos de Odoo; el mapeo a Odoo queda pendiente.

## 3. Convenciones

* Un ID es texto estable; no representa la posición de una fila. Los prefijos están en el [registro de identificadores](trazabilidad/identificadores-y-linaje.md).
* La fecha y hora de un evento incluye zona horaria o contexto.
* Los importes conservan moneda y unidad de precio.
* La obligatoriedad depende del evento, no de una ficha universal.
* Los datos `[SIM]` nunca sustituyen datos autorizados de la operación.
* El responsable se indica con el perfil del [modelo de autorización](../arquitectura/seguridad/modelo-autorizacion.md).

## 4. Campos

| Objeto.campo | Significado y tipo | Obligatorio | Responsable |
|---|---|---|---|
| Cuenta.id_cliente | Identidad interna; texto | Al crear la cuenta | R-ATN |
| Cuenta.nombre_razon_social | Nombre o referencia; texto | Al identificar la cuenta | R-ATN |
| Cuenta.documento_identidad | DNI/RUC si es pertinente; texto | Según la operación; no para todo lead | R-PRO |
| Contacto.id_contacto / id_cliente | Identidad y relación; texto | Al relacionar el contacto | R-ATN |
| Contacto.rol_contacto | Dueño, maestro, receptor u otro; categoría | Cuando participa en la operación | R-ATN |
| Contacto.telefono / canal_preferido | Medio operativo; texto o categoría | Cuando se necesita para contactar | R-ATN |
| Contacto.consentimiento_promocional | Conocido o desconocido, con soporte | Si se evalúa una promoción | R-PRO |
| Dirección.id_direccion / id_cliente | Identidad y cuenta; texto | Al guardar la dirección | R-ATN |
| Dirección.nombre_obra / ubicacion | Contexto y referencia; texto | Si aplica | R-ATN |
| Producto.id_producto / unidad_medida | Material y unidad de cotización | En cada producto | R-PRO |
| Oportunidad.id_oportunidad | Identidad comercial; texto | Al calificar el interés | R-ATN |
| Oportunidad.canal | Medio de la interacción: Presencial, WhatsApp, Teléfono | En cada interacción | R-ATN |
| Oportunidad.fuente | Procedencia: Referido maestro, Referido cliente, Cliente frecuente, Directo | Al conocerla | R-ATN |
| Oportunidad.campana | Campaña que causó la consulta: `CAM-01` a `CAM-04` o vacío ([catálogo de campañas](../procesos/comercial-crm/cuenta-contacto-canales.md#53-catálogo-de-campañas)) | Solo si la causó | R-ATN |
| Oportunidad.necesidad / responsable | Qué se busca y quién da seguimiento | Mientras esté abierta | R-ATN |
| Oportunidad.probabilidad | Baja, Media o Alta | Si se usa la escala | R-ATN |
| Oportunidad.proxima_accion / fecha | Acción y momento previsto | Oportunidad abierta (RN-02) | R-ATN |
| Oportunidad.resultado / motivo | Abierta, ganada total o parcial, perdida, y su causa | Al registrar el desenlace | R-ATN |
| Cotización.id_cotizacion / numero / version | Identidad de la emisión, familia y revisión | En cada propuesta (RN-04) | R-ATN |
| Cotización.id_oportunidad / fecha_emision | Origen y fecha | En cada emisión | R-ATN |
| Cotización.criterio_vigencia | Condición comunicada; texto | Antes de comunicarla | R-ATN / R-PRO |
| Cotización.tipo_comprobante_previsto | Boleta, factura o por definir | Cuando se acuerde (RN-06) | R-ATN |
| Detalle.linea / id_producto / cantidad | Línea de la versión, material y cantidad numérica | En cada línea | R-ATN |
| Detalle.precio_referencia / precio_ofrecido | Importes por unidad; numérico con moneda | En cada línea | R-ATN / R-PRO |
| Detalle.motivo_ajuste / autorizado_por | Razón y decisor | Cuando hay excepción (EXC-01) | R-PRO |
| Decisión.id_decision / objeto / fecha | Identidad, alcance y momento | En cada decisión relevante | R-PRO |
| Interacción.id_interaccion / referencia | Comunicación vinculada a cuenta u oportunidad | Cuando sustenta seguimiento o aceptación | R-ATN |
| Correlación.id_correlacion | Agrupa referencias de una operación entre sistemas | Solo si existe una interfaz externa (TR-13) | R-PRO |

## 5. Objetos transaccionales

Objetos que nacen y cambian durante cada operación. Los eventos que crean cada uno están en [INT-01](../arquitectura/integraciones/INT-01-CRM-ERP.md). No hay extractos operativos reales en el repositorio.

| Objeto | Origen / vínculo | Datos mínimos | Sistema | Regla |
|---|---|---|---|---|
| Consulta o interacción | Canal y contacto | Necesidad, fecha, responsable y referencia de comunicación | CRM | — |
| Oportunidad | Cuenta y contacto | Necesidad, madurez, competencia, acción y estado | CRM | RN-02 |
| Cotización y versión | Oportunidad | Fecha, líneas, precios, condiciones y versión | CRM | RN-03, RN-04 |
| Decisión comercial | Cotización o necesidad | Motivo, decisor, momento y condición | CRM | EXC-01 |
| Pedido | Versión aceptada | Cantidades, condiciones acordadas, soporte y estado | ERP | RN-08 |
| Recepción, entrega o ajuste | Compra o pedido; ubicación | Documento, cantidad real, pendiente, actor, fecha y diferencias | ERP | RN-09, RN-10 |
| Comprobante | Referencia de KeyFacil y pedido | Tipo, serie y número, importe y conciliación | KeyFacil / ERP | RN-11 |
| Pago | Comprobante | Soporte verificado, monto, aplicación y saldo | ERP | RN-12 |
| Caso posventa | Pedido de origen | Solicitud, decisión, ejecución y cierre | ERP | RN-13 |

Reglas de conservación:

* Cada objeto conserva su identificador y el enlace al anterior; el número de factura no se usa como ID de toda la operación ([registro de identificadores](trazabilidad/identificadores-y-linaje.md)).
* Una corrección relevante conserva valor anterior, posterior, motivo y actor.
* Los campos concretos de los objetos del ERP se detallarán y probarán al configurar cada módulo.

## 6. Pendientes

* El catálogo sintético usa la columna `origen`, que mezcla canal, fuente y campaña. Al ampliar el catálogo se separará en los tres campos de este diccionario.
* Mapeo de cada campo a Odoo.
* Política de retención de datos transaccionales; no se fijan plazos arbitrarios.

## 7. Historial de cambios

| Versión | Fecha | Autor | Cambio |
|---|---|---|---|
| 0.1 | 17/10/2026 | Brenda Mirano | Versión inicial; el diccionario pasa a ser la única fuente de definiciones e incorpora los objetos transaccionales |

Referencias: [catálogo sintético](pruebas/README.md), [clientes](maestros/clientes.md), [precios](maestros/precios.md), [fuentes](../fuentes/fuentes-negocio.md).
