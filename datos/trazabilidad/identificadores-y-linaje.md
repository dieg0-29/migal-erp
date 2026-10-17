# Identificadores y linaje de información

**Estado:** complemento conceptual propuesto del plan de trazabilidad; revisión con su responsable Luis pendiente. No implementa auditoría automática.

## Identidad y relaciones

| Identificador | Representa | Relación |
|---|---|---|
| id_cliente | Cuenta responsable | Agrupa contactos y contexto de obras |
| id_contacto | Interlocutor | Se relaciona con cuenta/operación pertinente |
| id_direccion | Dirección/obra | Contexto del cliente; futuro destino |
| id_oportunidad | Interés comercial | Cuenta/contacto y cotizaciones |
| numero_cotizacion + version | Familia y emisión | Una revisión no sustituye sin rastro a otra |
| id_decision | Decisión documentada | Oferta/línea/condición afectada |
| id_correlacion | Agrupación transversal propuesta en el plan de trazabilidad | Enlaza referencias; no reemplaza IDs propios |
| IDs de pedido/entrega/comprobante/pago | Documentos posteriores | Se incorporan solo cuando existan |

El prefijo SIM distingue ejemplos de referencias de operación. Los formatos CLI-SIM/OPP-SIM/COT-SIM son convenciones académicas, no secuencias garantizadas en Odoo. El plan de trazabilidad usa CORR-2026-0042 como otro ejemplo; no atribuirlo al catálogo CRM sin un mapeo explícito.

## Linaje mínimo

| Información | Procedencia | Transformación / conservación |
|---|---|---|
| Necesidad | Consulta del cliente/contacto | Resumen fiel vinculado a interacción; señalar incertidumbre |
| Cuenta/obra | Contexto levantado y ficha existente | Buscar, validar y relacionar; no fusionar automáticamente |
| Producto/unidad | Catálogo revisado | Seleccionar variante correcta; conservar línea cotizada |
| Precio ofrecido | Referencia y decisión propietaria | Capturar versión, motivo y autor de cambio |
| Seguimiento | Próximo paso comercial | Acción, fecha y responsable |
| Resultado | Respuesta o hecho comercial posterior | Fuente y motivo; no inferir compra de una cotización |

## Recorrido del caso normal

CLI-SIM-001 → CON-SIM-002 / DIR-SIM-001 → OPP-SIM-001 → COT-SIM-001-V01 → líneas PRD-SIM-001/002/003. No existe en este recorrido un pedido ni un comprobante. El soporte de comunicación y seguimiento debe obtenerse al ejecutar la prueba.

## Captura y corrección

Registrar objeto, acción, actor, fecha/hora con zona, anterior/posterior cuando corresponda, motivo y evidencia. Antes de una corrección revisar referencias dependientes; conservar motivo de consolidación o desactivación. No declarar registros inmutables si no se ha probado el mecanismo de protección. Un enlace roto se registra como incidencia, no se completa con un evento ficticio.

## Aplicabilidad del plan de trazabilidad

TR-01/02/03/04 cubren captación, calificación, cotización y aprobación cuando corresponda. TR-05 mezcla aceptación y pedido: aplicar solo la parte pertinente al corte y diferir confirmación. TR-06 a TR-11 corresponden a ejecución futura; TR-12 es transversal; TR-13 solo si existe interfaz aprobada. El [modelo de autorización](../../arquitectura/seguridad/modelo-autorizacion.md) y el plan de trazabilidad conservan sus códigos; este documento no crea otra numeración de controles.

Referencias: [plan de trazabilidad](plan-trazabilidad-auditoria.md), [frontera](../../procesos/comercial-crm/frontera-conceptual-crm-erp.md), [diccionario](../diccionario/diccionario-datos.md), [privacidad](../privacidad/tratamiento-datos.md).
