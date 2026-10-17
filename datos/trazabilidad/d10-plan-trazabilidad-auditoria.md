# Plan de trazabilidad y auditoría

> Documento convertido desde el adjunto oficial más reciente recibido para PC2; su contenido puede estar sujeto a cambios.


Ferre & Inversiones MIGAL  |  Escenario comercial CRM y ERP

| Responsable asignado | Estado | Documento asociado |
| --- | --- | --- |
| Luis Núñez | Modelo de trazabilidad para PC2 | [d10-matriz-trazabilidad.xlsx](d10-matriz-trazabilidad.xlsx) |

Se establece un modelo de trazabilidad que permite reconstruir una operación mediante su origen, responsables, decisiones, documentos, movimientos y resultados. El identificador de correlación relaciona las etapas, mientras la cotización, el pedido, la referencia fiscal y los registros de seguimiento conservan sus identificadores propios.

El diseño se apoya en los procesos de ventas e inventario y en las vistas C4 documentadas en la PC1. La matriz anexa [d10-matriz-trazabilidad.xlsx](d10-matriz-trazabilidad.xlsx) reúne TR-01 a TR-13, la relación RN–EV–CT–CP y el recorrido de auditoría.

## Propósito, alcance y vinculación

D10 organiza la reconstrucción desde la captación del lead y la calificación de la oportunidad hasta la cotización y su aceptación. También enlaza, como extensión del escenario integrado, pedido, reserva, entrega, comprobante KeyFacil, cobro, posventa y cierre. La PC1 documenta el flujo O2C, inventario, los componentes de Odoo y la frontera fiscal externa (PC1-01, PC1-05 a PC1-10).

La trazabilidad propuesta distingue hechos históricos del negocio, eventos técnicos y evidencias verificables. Los códigos y relaciones identificados en el repositorio de PC1 se registran en Referencias_PC1 de la matriz, con enlace a su versión consultada.

## Modelo de rastro y cadena de referencias

La historia del negocio conserva canal, responsable, etapas y decisiones que afectan el acuerdo con el cliente; la traza técnica vincula actor, objeto, acción, estado, resultado, error y reintento. Los comprobantes, capturas y exportaciones de una prueba actúan como soporte independiente de ambos historiales.

Cada evento TR incluye identificador, tipo, referencia del objeto, usuario o servicio, rol, fecha y hora con zona, acción y resultado. Para cambios críticos se conserva el valor anterior y posterior, el motivo, el correlation_id y la evidencia asociada. Cuando exista una interfaz externa con reintentos, se agregan idempotency_key y número de intento, sin almacenar credenciales ni datos personales innecesarios.

La cadena de referencia ilustrativa es lead → oportunidad → COT-2026-0042 → SO-2026-0042 → F001-004512 → posventa, con correlación CORR-2026-0042. Los identificadores corresponden a un caso sintético; la auditoría debe cotejar en cada entorno las referencias y transiciones que realmente produce Odoo y su relación con KeyFacil.

## Catálogo de eventos y controles de captura

El catálogo incorpora trece trazas, desde la captación hasta las operaciones de acceso e interfaz. Cada evento precisa momento, datos mínimos y vínculos con el control funcional. Su diseño responde a las necesidades del escenario comercial y a los procesos; el detalle se consigna en la hoja Mapa_TR.

| ID | Momento | Registro mínimo |
| --- | --- | --- |
| TR-01 | Lead y duplicado | Alta, canal, actor, hora, contacto y resultado del cotejo de duplicados. |
| TR-02 | Calificación y oportunidad | Cambio de etapa, responsable y vínculo lead–oportunidad. |
| TR-03 | Cotización y precio | Versión, líneas, importes, valores anterior/posterior y motivo. |
| TR-04 | Aprobación comercial | Solicitante, aprobador diferente, decisión y fundamento. |
| TR-05 | Aceptación y pedido | Aceptación, condición acordada, validación y resultado. |
| TR-06 | Stock y reserva | Pedido, ubicación, cantidades solicitada y reservada. |
| TR-07 | Entrega física | Documento de salida, operador, unidades entregadas y diferencias. |
| TR-08 | Comprobante y conciliación | Referencia KeyFacil, monto fiscal, fecha y conciliación. |
| TR-09 | Cobro | Soporte de pago, fecha, saldo previo y resultante. |
| TR-10 | Posventa | Caso, motivo, responsable, decisión y cierre. |
| TR-11 | Cierre operativo | Pendientes atendidos, validación y responsable. |
| TR-12 | Acceso y cambios sensibles | Usuarios, perfiles, cambios autorizados y exportes. |
| TR-13 | Interfaz y reintentos | Correlación, operación, estado, error y reintento, si aplica. |

## Registro de eventos, integridad y protección

En Odoo se utilizarán los registros funcionales, seguimiento de campos y referencias disponibles según la configuración efectiva. Para cambios sensibles en precio, aceptación, crédito, permisos y stock, la verificación comparará estado anterior y posterior y capturará actor, momento y resultado. El historial y los archivos de evidencia se conservarán vinculados al caso de prueba.

El diagrama de componentes sitúa ventas e inventario en el mismo entorno ERP; por ello, una transición interna se reconstruye mediante objetos y sus estados. KeyFacil constituye un sistema externo y su comprobante se enlaza con el pedido mediante una referencia fiscal y la conciliación de importes. Una interfaz adicional, si existe, registra solicitud, respuesta, error e intento de recuperación.

El modelo preserva la atribución individual, el acceso mínimo por rol, la exportación controlada y el seguimiento de rectificaciones. Una corrección se documenta como nuevo hecho referido al anterior. Para comprobar integridad se asocia al paquete de evidencias una huella digital y se limita la edición de los registros de auditoría.

## Acceso, custodia y minimización de información

| Perfil D09 | Detalle permitido en D10 | Límite |
| --- | --- | --- |
| Atención comercial · PR-02 | Historial de operaciones propias o asignadas. | Sin acceso general a información fiscal o crediticia. |
| Propietario · PR-04 | Decisiones, aprobaciones y revisión global. | Exportación extraordinaria justificada y registrada. |
| Almacén · PR-05 | Reserva, entrada y salida física requeridas. | Sin lectura de crédito ni negociaciones ajenas. |
| Facturación · PR-06 | Comprobantes, pagos y conciliación a cargo. | Sin datos comerciales innecesarios. |
| Técnico · PR-07 | Metadatos, incidencias y cambios de permisos. | Sin edición ordinaria de negocio o eliminación de evidencia. |
| Servicio · PR-08 | Eventos técnicos mínimos de interfaz, si existe. | Sin acceso interactivo o borrado de registros. |

El acceso al rastro depende de la función: atención comercial consulta los casos a su cargo; propietarios supervisan las decisiones; almacén revisa movimientos necesarios; facturación coteja comprobantes y cobros; soporte técnico accede a metadatos operativos. El período de conservación y los procedimientos de archivo se establecerán por clase de registro, conforme a la política aprobada por los responsables.

## Relación RN, EV, CT, CP y antecedentes

La hoja RN_EV_CT_CP articula reglas de negocio, eventos, controles, casos de prueba y trazas. En su columna de antecedente se citan archivos verificables del repositorio; así se identifica qué parte del modelo proviene del análisis anterior y qué control se incorporará. Los casos CP-01 y CP-02 permiten verificar cada relación con datos sintéticos.

Una prueba se considera documentada cuando incluye versión y módulos, usuario o perfil, datos de entrada, resultado esperado, resultado obtenido, referencia de captura y estado. Si el enlace CRM–ERP es una transición interna, se audita el cambio de objeto/estado, sin suponer una llamada HTTP.

## Auditoría de una operación y gestión de excepciones

La hoja Auditoria_CP01 propone nueve comprobaciones consecutivas del caso ilustrativo: localizar operación, recuperar lead y oportunidad, examinar cotización, validar aprobaciones, enlazar pedido, revisar stock y entrega, conciliar comprobante y cobro, verificar posventa y confirmar integridad. En cada paso se anota la evidencia encontrada y el resultado.

Los eventos de excepción conservan su solicitud, actor, motivo y resolución: duplicados, cambios de precio, crédito, falta de stock, entrega parcial, descuadres de comprobante o reintentos. Si el comportamiento observado se aparta del esperado, se crea una incidencia relacionada con el caso de prueba y se conserva la evidencia del resultado real.

## Referencias documentales de la PC1

| Referencia PC1 | Documento / aspecto | Aplicación en D10 |
| --- | --- | --- |
| PC1-01 | Contexto de empresa | KeyFacil, canales y registros actuales. |
| PC1-03 | ADR-002 | Selección de Odoo 18 Community. |
| PC1-05 | C4: contexto | Límite ERP, WhatsApp y plataforma fiscal. |
| PC1-06 | C4: contenedores | Módulos, usuarios y base de datos. |
| PC1-07 | C4: ventas | Cotización, orden, POS y facturación externa. |
| PC1-08 | C4: inventario | Movimientos y objetos de stock. |
| PC1-09 / PC1-10 | Flujos de ventas e inventario | Estados y documentos de origen/destino. |
| PC1-11 / PC1-12 | Riesgos y backlog | Verificación de controles y actividades previstas. |

Los enlaces exactos de PC1 figuran en Referencias_PC1 de la matriz D10.
