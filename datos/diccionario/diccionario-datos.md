# Diccionario de datos

## 1. Metadatos

* **Fecha:** 17/10/2026
* **Versión:** 0.1
* **Autores:** Brenda Mirano
* **Custodio:** R-PRO

## 2. Propósito

Este diccionario es la única fuente de definiciones de campos del proyecto. Las fichas de entidad, el catálogo sintético y los casos de prueba usan estos nombres. No diseña tablas ni garantiza campos nativos de Odoo; el mapeo a Odoo queda pendiente.

## 3. Convenciones

* Un ID es texto estable; no representa la posición de una fila. Los prefijos están en el [registro de identificadores](../trazabilidad/identificadores-y-linaje.md).
* La fecha y hora de un evento incluye zona horaria o contexto.
* Los importes conservan moneda y unidad de precio.
* La obligatoriedad depende del evento, no de una ficha universal.
* Los datos `[SIM]` nunca sustituyen datos autorizados de la operación.
* El responsable se indica con el perfil del [modelo de autorización](../../arquitectura/seguridad/modelo-autorizacion.md).

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
| Oportunidad.campana | Campaña que causó la consulta: `CAM-01` a `CAM-04` o vacío ([catálogo de campañas](../../procesos/comercial-crm/cuenta-contacto-canales.md#53-catálogo-de-campañas)) | Solo si la causó | R-ATN |
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

## 5. Campos de eventos posteriores (ERP)

| Objeto | Datos mínimos | Regla |
|---|---|---|
| Pedido | Cotización aceptada, cantidades, condiciones y estado | RN-08 |
| Entrega | Documento, ubicación, cantidad real y pendiente | RN-10 |
| Comprobante | Emisor externo, tipo, serie y número, importe | RN-11 |
| Pago | Soporte verificado, monto, aplicación y saldo | RN-12 |
| Proveedor | Identidad y referencia de compra | Ver [proveedores](../maestros/proveedores.md) |

Los campos concretos se detallarán y probarán al configurar cada módulo del ERP.

## 6. Pendientes

* El catálogo sintético usa la columna `origen`, que mezcla canal, fuente y campaña. Al ampliar el catálogo se separará en los tres campos de este diccionario.
* Mapeo de cada campo a Odoo.

## 7. Historial de cambios

| Versión | Fecha | Autor | Cambio |
|---|---|---|---|
| 0.1 | 17/10/2026 | Brenda Mirano | Versión inicial; el diccionario pasa a ser la única fuente de definiciones |

Referencias: [catálogo sintético](../pruebas/README.md), [clientes](../maestros/clientes.md), [precios](../maestros/precios.md), [fuentes](../../fuentes/fuentes-negocio.md).
