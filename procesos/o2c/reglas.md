# Reglas funcionales de Order to Cash

**Estado:** TO-BE propuesto. Los IDs `O2C-R-*` complementan D10 sin redefinir sus códigos RN.

| ID | Regla | Momento y responsable funcional | Evidencia / respuesta a excepción |
|---|---|---|---|
| O2C-R-01 | Identificar interlocutor y relación sin exigir DNI/RUC para toda consulta | Atención, captación | Referencia de cuenta/contacto o dato pendiente |
| O2C-R-02 | Cotizar producto, unidad, cantidad y precio explícitos | Atención, preparación | Líneas revisables; aclarar variante antes de enviar |
| O2C-R-03 | Conservar nueva versión ante cambio relevante de oferta | Quien cotiza | Anterior/posterior, causa y fecha |
| O2C-R-04 | Registrar excepción de precio y decisión propietaria | Propietarios, negociación | Motivo, referencia/ofrecido y autorizador; revisión cruzada D09 propuesta por validar |
| O2C-R-05 | No prometer disponibilidad/fecha sin fundamento o condición explícita | Propietarios/Atención | Información revisada, condición y responsable; pendiente si incierto |
| O2C-R-06 | No convertir propuesta no aceptada en pedido | Atención, futuro | Versión, actor y soporte de aceptación; validar representación en Odoo |
| O2C-R-07 | Separar cantidad solicitada, reservada y realmente entregada | Operación, futuro | Documento y ubicación; saldo pendiente en parcial |
| O2C-R-08 | Distinguir documento interno y comprobante KeyFacil | Propietarios, futuro | Referencia externa y conciliación; no asumir emisión automática |
| O2C-R-09 | Registrar pago únicamente como verificado antes de aplicarlo | Propietarios, futuro | Soporte, monto, aplicación y saldo; discrepancia pendiente |
| O2C-R-10 | Cerrar con pendientes resueltos o excepción identificada | Responsable funcional, futuro | Entrega/cobro/casos y motivo de cierre |

## Reglas de negocio y configuración

No se fijan descuento máximo, vigencia de tres días, crédito ni tarifa de reparto sin validación. Solicitar aceptación y revisión es una propuesta funcional; no significa que exista bloqueo técnico. La forma de reservar, actualizar stock POS, facturar por pedido/entregado y contabilizar debe definirse y probarse en el entorno.

## Alcance y trazabilidad

R-01 a R-05 corresponden al escenario PC2; R-06 a R-10 son etapa futura. Una oportunidad ganada por compra efectiva requiere evidencia posterior y no se prueba solo con cotización. Registrar referencias a D09/D10 cuando se revisen sus controles, conservando su responsable Luis.

## Aceptación

Cada regla se acepta con caso, datos SIM, esperado/obtenido, usuario/rol y evidencia. Estado actual: propuesta, ejecución pendiente. Fuentes: [decisiones comerciales](../comercial-crm/decisiones-comerciales.md), [supuestos](../../fuentes/supuestos-y-vacios.md), [D09](../../arquitectura/seguridad/d09-autorizacion-y-segregacion.md).
