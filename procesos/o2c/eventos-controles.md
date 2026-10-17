# Eventos y controles — O2C

**Estado:** hitos de negocio y controles propuestos. No son mensajes publicados ni APIs implementadas. Namespace `O2C-E/C` independiente del catálogo del plan de trazabilidad.

| Evento | Control y condición de avance | Evidencia mínima | Correspondencia en el plan de trazabilidad | Corte |
|---|---|---|---|---|
| O2C-E-01 Consulta registrada | O2C-C-01: buscar contacto/cuenta y asignar atención | Necesidad, canal/fuente, referencia y responsable | TR-01 | PC2 |
| O2C-E-02 Oportunidad calificada | O2C-C-02: conservar señales de interés y siguiente acción | Cuenta/contacto, necesidad y madurez | TR-02 | PC2 |
| O2C-E-03 Cotización preparada/revisada | O2C-C-03: líneas, unidades, condiciones y versión | Valores y causa de cambio | TR-03 | PC2 |
| O2C-E-04 Excepción comercial decidida | O2C-C-04: aprobación requerida y separación propuesta en el [modelo de autorización](../../arquitectura/seguridad/modelo-autorizacion.md) | Iniciador, decisor, motivo, fecha | TR-04 | PC2 si aplica |
| O2C-E-05 Aceptación registrada | O2C-C-05: cotejar versión y condiciones antes de confirmar | Quién acepta y soporte | Parte de TR-05 | Futuro; frontera |
| O2C-E-06 Reserva/preparación | O2C-C-06: ubicación y cantidad verificables | Pedido y cantidades por estado | TR-06 | Futuro |
| O2C-E-07 Entrega registrada | O2C-C-07: cantidad real y diferencia | Salida y recepción/conformidad pertinente | TR-07 | Futuro |
| O2C-E-08 Referencia fiscal registrada | O2C-C-08: cotejar operación e importe | KeyFacil y conciliador | TR-08 | Futuro |
| O2C-E-09 Pago aplicado | O2C-C-09: verificar soporte y evitar doble aplicación | Monto, operación y saldo | TR-09 | Futuro |
| O2C-E-10 Cierre revisado | O2C-C-10: resolver pendientes o documentar excepción | Estado y responsable de cierre | TR-10/11 si aplica | Futuro |

## Responsabilidad y tratamiento de fallas

Atención ejecuta controles comerciales; propietarios deciden excepciones; almacén documenta preparación/entrega; propietarios realizan emisión/cobro según función. Una condición incumplida genera pendiente con causa y responsable. No se borra la operación ni se sustituye evidencia con un resultado esperado.

## Prueba documental propuesta

Seguir COT-SIM-001-V01 desde OPP-SIM-001 y revisar C-01/02/03. Para excepción, verificar versión, precio y autorización sin afirmar implementación de SOD. Las filas futuras requieren casos propios y entorno cuando corresponda. No se asignan CP-01/02 nuevos para evitar conflicto con Luis.

Referencias: [reglas O2C](reglas.md), [plan de trazabilidad](../../datos/trazabilidad/plan-trazabilidad-auditoria.md), [linaje](../../datos/trazabilidad/identificadores-y-linaje.md), [fuentes](../../fuentes/fuentes-negocio.md).
