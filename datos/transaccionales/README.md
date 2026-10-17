# Datos transaccionales por etapa

**Estado:** catálogo conceptual TO-BE. No hay extractos operativos reales en esta carpeta.

## Objetos

| Objeto | Origen / vínculo | Datos mínimos propuestos | Corte |
|---|---|---|---|
| Consulta/interacción | Canal y contacto | Necesidad, fecha, responsable y referencia de comunicación | PC2; registro propuesto |
| Oportunidad | Cuenta/contacto | Necesidad, madurez, competencia, acción y estado | PC2 |
| Cotización/versión | Oportunidad | Fecha, líneas, precios, condiciones y versión | PC2 |
| Decisión comercial | Cotización o necesidad | Motivo, decisor, momento y condición | PC2 |
| Pedido | Versión y aceptación | Cantidades/condiciones acordadas y soporte | Futuro |
| Recepción/entrega/ajuste | Compra o pedido; ubicación | Cantidad real, documento, actor, fecha y diferencias | Futuro |
| Comprobante | Referencia KeyFacil y operación | Tipo, serie/número, importe y conciliación | Futuro |
| Pago/aplicación | Obligación o comprobante | Soporte verificado, monto y saldo | Futuro |
| Caso posventa | Operación de origen | Solicitud, decisión, ejecución y cierre | Futuro |

## Reglas de conservación

Conservar identificadores propios y enlaces entre objetos; no reutilizar el número de factura como ID de toda la operación. Una corrección relevante conserva anterior, posterior, motivo y actor. No confundir campos cambiantes con evidencia histórica. El mecanismo real de versionado y seguimiento se validará en el entorno elegido.

Los ejemplos académicos usan SIM. No subir conversaciones privadas, comprobantes reales, cuentas o datos crediticios sin autorización y minimización. La política de retención sigue pendiente; no establecer plazos arbitrarios.

## Aceptación y pendientes

Una muestra es utilizable si declara alcance, origen, definición de campos, IDs, reglas, relación con caso de prueba y anonimización/simulación. Pendientes: definición física/importación, mecanismos de captura y campos adicionales por hito.

Referencias: [diccionario](../diccionario/diccionario-datos.md), [linaje](../trazabilidad/identificadores-y-linaje.md), [plan de trazabilidad](../trazabilidad/plan-trazabilidad-auditoria.md), [privacidad](../privacidad/tratamiento-datos.md).
