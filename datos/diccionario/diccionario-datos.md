# Diccionario conceptual de datos

**Estado:** índice canónico propuesto para revisión de Datos. Complementa `Diccionario_CRM` del Excel existente; no diseña tablas ni garantiza campos nativos de Odoo.

## Convenciones

ID es texto estable; no representa posición de fila. Fecha/hora de eventos debe incluir zona o contexto horario. Importes conservan moneda y unidad de precio; no se mezclan con fechas. Obligatoriedad depende de etapa, no de una ficha universal. Datos SIM nunca sustituyen datos autorizados de operación.

| Objeto/campo | Significado y tipo conceptual | Exigencia propuesta | Responsable funcional |
|---|---|---|---|
| Cuenta.id_cliente | Identidad interna, texto | Al crear cuenta | Quien registra |
| Cuenta.nombre_razon_social | Nombre/referencia, texto | Al identificar cuenta | Atención |
| Cuenta.documento_identidad | DNI/RUC si pertinente, texto | Según operación; no todo lead | Propietarios |
| Contacto.id_contacto / id_cliente | Identidad y relación, texto | Al relacionar contacto | Atención |
| Contacto.rol_contacto | Dueño, maestro, receptor u otro, categoría | Cuando participa en operación | Atención |
| Contacto.telefono / canal_preferido | Medio operativo, texto/categoría | Cuando necesario para contacto | Atención |
| Contacto.consentimiento_promocional | Estado conocido/desconocido y soporte | Si se evalúa promoción | Propietarios |
| Dirección.id_direccion / id_cliente | Identidad y cuenta, texto | Al guardar dirección | Atención |
| Dirección.nombre_obra / ubicacion | Contexto y referencia, texto | Si aplica | Quien coordina |
| Producto.id_producto / unidad_medida | Material y unidad de cotización | Cada línea de catálogo | Propietarios/Datos |
| Oportunidad.id_oportunidad | Identidad comercial, texto | Al calificar interés | Atención |
| Oportunidad.canal | Medio de la interacción: Presencial, WhatsApp, Teléfono | En cada interacción | Atención |
| Oportunidad.fuente | Procedencia: Referido maestro, Referido cliente, Cliente frecuente, Directo | Al conocerla; indicar pendiente | Atención |
| Oportunidad.campana | Iniciativa que causó la consulta: `CAM-01` a `CAM-04` o vacío (ver catálogo en `cuenta-contacto-canales.md` §5.3) | Solo si el cliente la menciona o es evidente | Atención |
| Oportunidad.necesidad / responsable | Qué se busca / quién sigue | Mientras esté abierta | Atención |
| Oportunidad.probabilidad | Baja/Media/Alta | Si se utiliza escala | Responsable comercial |
| Oportunidad.proxima_accion / fecha | Acción y momento previsto | Oportunidad abierta con seguimiento | Responsable comercial |
| Oportunidad.resultado / motivo | Abierta, ganada total/parcial, perdida / causa | Al registrar desenlace | Responsable comercial |
| Cotización.id_cotizacion / numero / version | Identidad de emisión, familia y revisión | Cada propuesta conservada | Quien cotiza |
| Cotización.id_oportunidad / fecha_emision | Origen y fecha | Cada emisión | Quien cotiza |
| Cotización.criterio_vigencia | Condición comunicada, texto | Antes de comunicar | Propietarios/Atención |
| Cotización.tipo_comprobante_previsto | Boleta/factura/por definir | Cuando se acuerde | Atención |
| Detalle.linea / id_producto / cantidad | Identidad en versión, material y cantidad numérica | Cada línea | Quien cotiza |
| Detalle.precio_referencia / ofrecido | Importes por unidad, numérico + moneda | Cada línea | Propietarios/Atención |
| Detalle.motivo_ajuste / autorizado_por | Razón y decisor, texto/referencia | Cuando hay excepción | Propietarios |
| Decisión.id_decision / objeto / fecha | Identidad, alcance y momento | Decisión relevante | Quien documenta |
| Interacción.id_interaccion / referencia | Comunicación vinculada a cuenta/oportunidad, propuesta | Cuando sustenta seguimiento/aceptación | Atención |
| Correlación.id_correlacion | Enlace transversal de referencias, propuesta en el plan de trazabilidad | Al reconstruir caso integrado | Responsable de trazabilidad |

## Extensión posterior

Pedido: referencia de cotización aceptada, cantidades, condiciones y estado. Entrega: documento, ubicación, cantidad real y pendiente. Comprobante: emisor externo, tipo, serie/número e importe. Pago: soporte verificado, monto, aplicación y saldo. Proveedor: identidad y referencia de compra. Los campos concretos se detallarán y probarán en la fase operativa; no se imponen a PC2.

## Diferencias respecto al catálogo recibido

El Excel dispone de 25 entradas en `Diccionario_CRM` y columnas adicionales de contexto. Este documento organiza sus conceptos y propone separar canal, fuente y campaña (la columna `origen` del Excel mezcla los tres); no afirma que existan columnas de interacción, correlación o canal separado en el libro. El mapeo de campos y relaciones a Odoo queda pendiente de revisión. No editar simultáneamente definiciones divergentes: un cambio debe registrarse aquí y en el catálogo si se adopta.

Referencias: [catálogo](../pruebas/README.md), [maestros de clientes](../maestros/clientes.md), [precios](../maestros/precios.md), [linaje](../trazabilidad/identificadores-y-linaje.md), [fuentes](../../fuentes/fuentes-negocio.md).
