# Facturación y referencia externa

**Estado:** diseño funcional; no es procedimiento tributario aprobado ni integración implementada. Forma parte del [flujo O2C](flujo.md), pasos 5 y 6.

## Frontera

Hasta la aceptación, el CRM conserva solo el comprobante previsto y la información fiscal disponible o pendiente (RN-06). Según ADR-004 y las fuentes del repositorio, KeyFacil permanece como emisor externo operado por propietarios. Un documento interno de Odoo y su número no se presentan automáticamente como comprobante fiscal válido.

## Datos y responsabilidades

R-PRO comprueba la operación y datos necesarios, opera KeyFacil y conserva referencia del comprobante. R-FAC concilia importe y relación con pedido/entrega según la política validada. R-ATN consulta solo el estado necesario; R-ALM no requiere detalle fiscal/crediticio general.

| Dato propuesto | Uso |
|---|---|
| Operación / pedido de origen | Evitar referencia fiscal sin contexto |
| Emisor/sistema, tipo y serie/número | Identificar comprobante externo |
| Fecha, moneda e importe | Conciliar contra lo acordado |
| Estado y responsable de conciliación | Distinguir registrado, revisado y discrepante |
| Referencia de corrección/anulación si aplica | Reconstruir el cambio sin borrar original |

## Flujo propuesto

1. Recuperar operación, condiciones y soporte pertinente.
2. Completar datos requeridos según procedimiento fiscal validado por responsable competente.
3. Emitir en KeyFacil por propietario autorizado.
4. Registrar referencia en el soporte operativo definido; el campo/mecanismo está pendiente.
5. Comparar cliente, moneda, importe y relación con operación; registrar diferencia si existe.
6. Gestionar correcciones con autorización, evidencia y procedimiento aplicable, conservando original.

## Controles y excepciones

No emitir dos veces por falta de referencia o reintento manual; buscar comprobante existente. No confundir emisión con cobro. Si hay importe o identidad discrepante, mantener revisión y documentar resolución; no corregir silenciosamente la cotización para hacerla coincidir. El [modelo de autorización](../../arquitectura/seguridad/modelo-autorizacion.md) propone revisión independiente para anulación; validar viabilidad y no asumir bloqueo técnico.

## Pendientes y aceptación

Validar requisitos fiscales, momento de emisión, política respecto a entregas/pagos anticipados, campos de referencia y conciliación. La prueba futura deberá mostrar referencia única y diferencia resuelta con datos SIM. No se declara cumplimiento tributario ni resultado de prueba.

Referencias: [decisiones comerciales](../comercial-crm/decisiones-comerciales.md), [ADR-004](../../arquitectura/decisiones/ADR-004-odoo-community-fronteras-crm-erp.md), [modelo de autorización](../../arquitectura/seguridad/modelo-autorizacion.md), [plan de trazabilidad](../../datos/trazabilidad/plan-trazabilidad-auditoria.md), [fuentes](../../fuentes/fuentes-negocio.md).
