# Plan de trazabilidad y auditoría

Ferre & Inversiones MIGAL  |  Escenario comercial CRM y ERP

| Responsable asignado | Estado | Documento asociado |
| --- | --- | --- |
| Luis Núñez | Modelo de trazabilidad propuesto | [matriz-trazabilidad.xlsx](matriz-trazabilidad.xlsx) |

Se establece un modelo de trazabilidad que permite reconstruir una operación mediante su origen, responsables, decisiones, documentos, movimientos y resultados. El identificador de correlación relaciona las etapas, mientras la cotización, el pedido, la referencia fiscal y los registros de seguimiento conservan sus identificadores propios.

El diseño se apoya en los procesos de ventas e inventario y en las [vistas C4](../../arquitectura/vistas/consolidado-diagramas.md) de la arquitectura. La matriz anexa [matriz-trazabilidad.xlsx](matriz-trazabilidad.xlsx) reúne TR-01 a TR-13, la relación RN–EV–CT–CP y el recorrido de auditoría.

## Propósito, alcance y vinculación

Este plan organiza la reconstrucción desde la captación del lead y la calificación de la oportunidad hasta la cotización y su aceptación. También enlaza, como extensión del escenario integrado, pedido, reserva, entrega, comprobante KeyFacil, cobro, posventa y cierre. El repositorio documenta el [flujo O2C](../../procesos/o2c/flujo.md), el [flujo de inventario](../../procesos/inventario/flujo.md), los componentes de Odoo y la frontera fiscal externa ([ADR-004](../../arquitectura/decisiones/ADR-004-odoo-community-fronteras-crm-erp.md)).

La trazabilidad propuesta distingue hechos históricos del negocio, eventos técnicos y evidencias verificables.

## Modelo de rastro y cadena de referencias

La historia del negocio conserva canal, responsable, etapas y decisiones que afectan el acuerdo con el cliente; la traza técnica vincula actor, objeto, acción, estado, resultado, error y reintento. Los comprobantes, capturas y exportaciones de una prueba actúan como soporte independiente de ambos historiales.

Cada evento TR incluye identificador, tipo, referencia del objeto, usuario o servicio, rol, fecha y hora con zona, acción y resultado. Para cambios críticos se conserva el valor anterior y posterior, el motivo, el correlation_id y la evidencia asociada. Cuando exista una interfaz externa con reintentos, se agregan idempotency_key y número de intento, sin almacenar credenciales ni datos personales innecesarios.

La cadena de referencia ilustrativa es `OPP-SIM-001` → `COT-SIM-001-V01` → `PED-SIM-001` → `ENT-SIM-001` → `CPE-SIM-001` → `PAG-SIM-001` → posventa, con los prefijos del [registro de identificadores](identificadores-y-linaje.md). Los identificadores corresponden a un caso sintético; la auditoría debe cotejar en cada entorno las referencias y transiciones que realmente produce Odoo y su relación con KeyFacil.

## Catálogo de eventos y controles de captura

Las tablas de este documento son la fuente de verdad; la [matriz de trazabilidad](matriz-trazabilidad.xlsx) es una copia en Excel que se actualiza desde ellas. El catálogo incorpora trece trazas, desde la captación hasta las operaciones de acceso e interfaz. Cada evento precisa momento, datos mínimos y vínculos con el control funcional. Su diseño responde a las necesidades del escenario comercial y a los procesos; el detalle se consigna en la tabla siguiente.

| ID | Hito | Evento (INT) | Registro previsto | Contenido mínimo | Cadena documental | Perfil autorizado |
|---|---|---|---|---|---|---|
| TR-01 | Lead y duplicado | INT-01/EV-03 | Odoo · diseño funcional | Alta, canal, autor, fecha, vínculo al contacto; intento duplicado y resolución. | Lead / cliente | PR-02 / PR-04 |
| TR-02 | Calificación y oportunidad | INT-01/EV-05 | Odoo · diseño funcional | Cambio de etapa, responsable, motivo de descarte y relación lead–oportunidad. | Lead / oportunidad | PR-02 / PR-04 |
| TR-03 | Cotización y precio | INT-01/EV-06, EV-10 | Odoo · diseño funcional | Versión, líneas, precio anterior/nuevo, motivo, autor y destinatario. | Oportunidad / cotización | PR-02 / PR-04 |
| TR-04 | Aprobación comercial | INT-01/EV-09 | Odoo · diseño funcional | Solicitud, decisión, iniciador, aprobador distinto, fecha y fundamento. | Cotización / aprobación | PR-04 |
| TR-05 | Aceptación y pedido | INT-01/EV-11 | Odoo · diseño funcional | Aceptación documentada, condición de pago, validaciones y resultado; rechazos por crédito. | Cotización / pedido | PR-02 / PR-04 |
| TR-06 | Stock y reserva | Por definir (ERP) | Odoo · diseño funcional | Pedido, almacén, cantidad solicitada/disponible/reservada y excepción. | Pedido / reserva | PR-05 / PR-04 |
| TR-07 | Entrega física | Por definir (ERP) | Odoo · diseño funcional | Guía o soporte, cantidad entregada/pendiente, operador, fecha y diferencia. | Pedido / entrega | PR-05 / PR-04 |
| TR-08 | Comprobante y conciliación | Por definir (ERP) | KeyFacil / ERP | Referencia KeyFacil, monto ERP/fiscal, fecha, conciliador y descuadre. | Pedido / comprobante | PR-06 / PR-04 |
| TR-09 | Cobro | Por definir (ERP) | Odoo · diseño funcional | Referencia de pago verificada, saldo anterior/nuevo, fecha y responsable. | Comprobante / pago | PR-06 / PR-04 |
| TR-10 | Posventa | Por definir (ERP) | Odoo · diseño funcional | Caso, motivo, decisión, ejecución, documentos vinculados y cierre. | Pedido / caso posventa | PR-02 / PR-04 |
| TR-11 | Cierre operativo | Por definir (ERP) | Odoo · diseño funcional | Comprobación de pendientes, conciliación y responsable del cierre. | Pedido / cierre | PR-02 / PR-04 |
| TR-12 | Accesos y cambios sensibles | Transversal | Odoo · diseño funcional | Alta/cambio/baja de usuarios, cambios de permisos, exportaciones y ajustes autorizados. | Usuario / cambio | PR-07 / PR-04 |
| TR-13 | Interfaz y reintentos | Transversal | Interfaz condicional | ID de correlación, llave de idempotencia si aplica, operación, estado, error, reintento y conciliación. | correlation_id / intento | PR-08 si procede |

## Registro de eventos, integridad y protección

En Odoo se utilizarán los registros funcionales, seguimiento de campos y referencias disponibles según la configuración efectiva. Para cambios sensibles en precio, aceptación, crédito, permisos y stock, la verificación comparará estado anterior y posterior y capturará actor, momento y resultado. El historial y los archivos de evidencia se conservarán vinculados al caso de prueba.

El diagrama de componentes sitúa ventas e inventario en el mismo entorno ERP; por ello, una transición interna se reconstruye mediante objetos y sus estados. KeyFacil constituye un sistema externo y su comprobante se enlaza con el pedido mediante una referencia fiscal y la conciliación de importes. Una interfaz adicional, si existe, registra solicitud, respuesta, error e intento de recuperación.

El modelo preserva la atribución individual, el acceso mínimo por rol, la exportación controlada y el seguimiento de rectificaciones. Una corrección se documenta como nuevo hecho referido al anterior. Para comprobar integridad se asocia al paquete de evidencias una huella digital y se limita la edición de los registros de auditoría.

## Acceso, custodia y minimización de información

El acceso al rastro sigue los perfiles y reglas PR del [modelo de autorización](../../arquitectura/seguridad/modelo-autorizacion.md): cada perfil consulta solo las operaciones a su cargo, R-PRO supervisa decisiones y exportaciones, y ninguna cuenta edita ni borra evidencia.

El período de conservación y los procedimientos de archivo se establecerán por clase de registro, conforme a la política aprobada por los responsables.

## Relación RN, EV, CT, CP y antecedentes

La siguiente tabla relaciona las reglas y controles del [catálogo de reglas](../../procesos/catalogo-reglas.md) con los eventos de [INT-01](../../arquitectura/integraciones/INT-01-CRM-ERP.md), los casos de prueba y las trazas.

| Regla (RN/EXC) | Evento (INT) | Control (CT/SOD) | Caso CP | Traza TR | Respaldo documental | Criterio del control propuesto | Nivel de verificación |
|---|---|---|---|---|---|---|---|
| RN-01 | INT-01/EV-03 | CT-01 | CP-01 / CP-02 | TR-01 | Contexto de la empresa / C4 contexto | Captar prospectos y registrar evaluación de duplicados sin identificación fiscal universal. | Control propuesto · CP planificado |
| RN-02 | INT-01/EV-05 | CT-02 | CP-01 | TR-02 | Decisiones comerciales | Toda oportunidad abierta tiene próxima acción, fecha y responsable. | Control propuesto · CP planificado |
| RN-03 / RN-04 | INT-01/EV-06, EV-10 | CT-03 / CT-04 | CP-01 / CP-02 | TR-03 | Flujo O2C / C4 componentes ventas | Versionar y atribuir cada cambio relevante en el precio ofrecido. | Control propuesto · CP planificado |
| EXC-01 | INT-01/EV-08, EV-09 | SOD-01 | CP-02 | TR-04 | Flujo O2C | Separar iniciador y propietario aprobador de excepción comercial. | Control propuesto · CP planificado |
| RN-05 | INT-01/EV-07 | CT-05 | CP-01 | TR-03 | Decisiones comerciales | Solo personal autorizado confirma disponibilidad o fecha al cliente. | Control propuesto · CP planificado |
| RN-06 | INT-01/EV-06 | CT-06 | CP-01 | TR-03 | Decisiones comerciales | Registrar el comprobante previsto sin exigir RUC para cotizar. | Control propuesto · CP planificado |
| RN-07 | INT-01/EV-11 | CT-07 | CP-01 / CP-02 | TR-02 / TR-05 | Contexto de la empresa / Flujo O2C | Identificar cliente según necesidad de la transacción y mantener origen del dato. | Control propuesto · CP planificado |
| RN-08 | INT-01/EV-11 | CT-08 | CP-01 / CP-02 | TR-05 | Flujo O2C / C4 componentes ventas | Vincular aceptación del cliente con cotización y pedido; conservar versión. | Control propuesto · CP planificado |
| RN-09 | Por definir (ERP) | CT-09 | CP-01 / CP-02 | TR-06 | Flujo de inventario / C4 componentes inventario | Relacionar pedido y reserva con disponibilidad por ubicación. | Control propuesto · CP planificado |
| RN-10 | Por definir (ERP) | CT-10 | CP-01 / CP-02 | TR-07 | Flujo de inventario / C4 componentes inventario | Conservar cantidades realmente entregadas y diferencias físicas. | Control propuesto · CP planificado |
| RN-11 | Por definir (ERP) | CT-11 | CP-01 / CP-02 | TR-08 | Contexto de la empresa / C4 contexto | Conciliar referencia fiscal KeyFacil con pedido y valores correspondientes. | Control propuesto · CP planificado |
| RN-12 | Por definir (ERP) | CT-12 | CP-01 | TR-09 | Contexto de la empresa / Flujo O2C | Documentar cada cobro verificable y el saldo restante. | Control propuesto · CP planificado |
| RN-13 | Por definir (ERP) | CT-13 | CP-01 / CP-02 | TR-10 | Extensión futura (posventa) | Relacionar caso de atención posterior con pedido de origen. | Control propuesto · CP planificado |
| RN-14 | Por definir (ERP) | CT-14 | CP-01 | TR-11 | Riesgos y controles / Flujo O2C | Verificar cierre con entrega, cobro, incidencias y conformidad requerida. | Control propuesto · CP planificado |
| RN-15 | Por definir (ERP) | CT-15 | CP-02 | TR-05 | Contexto de la empresa (crédito actual) | Registrar decisión expresa de condiciones de crédito por propietario. | Control propuesto · CP planificado |

 Los casos CP-01 y CP-02 permiten verificar cada relación con datos sintéticos.

Una prueba se considera documentada cuando incluye versión y módulos, usuario o perfil, datos de entrada, resultado esperado, resultado obtenido, referencia de captura y estado. Si el enlace CRM–ERP es una transición interna, se audita el cambio de objeto/estado, sin suponer una llamada HTTP.

## Auditoría de una operación y gestión de excepciones

La auditoría del caso normal (CP-01) propone nueve comprobaciones consecutivas: localizar operación, recuperar lead y oportunidad, examinar cotización, validar aprobaciones, enlazar pedido, revisar stock y entrega, conciliar comprobante y cobro, verificar posventa y confirmar integridad. En cada paso se anota la evidencia encontrada y el resultado.

| Paso | Verificación | Actividad de auditoría | Evidencia requerida | Estado |
|---|---|---|---|---|
| 1 | Localizar caso | Abrir el caso por `OPP-SIM-001` [SIM] (cuenta `CLI-SIM-001`); anotar entorno, usuario auditor y fecha. | Cadena de identificadores del catálogo sintético. | Por ejecutar |
| 2 | Lead y oportunidad | Recuperar ID de lead y oportunidad, canal, responsable y cambios de etapa. | IDs y TR-01/02; por identificar en caso de prueba. | Por ejecutar |
| 3 | Cotización | Abrir `COT-SIM-001-V01`, versiones, líneas, precio y aceptación. | TR-03; soporte de aceptación; política de vigencia vigente. | Por ejecutar |
| 4 | Aprobaciones | Si hubo excepción, comparar iniciador y aprobador, motivo y fecha. | TR-04 y PR-04; si no hubo, marcar N/A. | Por ejecutar |
| 5 | Pedido | Seguir el pedido `PED-SIM-001` [SIM] desde la aceptación, cuando exista; revisar respuesta y llave de reintento si existe interfaz. | TR-05/13; no asumir una orden separada en Odoo. | Por ejecutar |
| 6 | Stock y entrega | Cotejar reserva por almacén y soporte de salida con cantidades pendientes. | TR-06/07; documento de entrega y diferencia. | Por ejecutar |
| 7 | Comprobante y cobro | Comparar pedido, comprobante `CPE-SIM-001` [SIM] en KeyFacil, monto y pago por separado. | TR-08/09; exporte o captura fiscal y conciliación. | Por ejecutar |
| 8 | Posventa y cierre | Buscar caso posventa, revisar pendientes y motivo de cierre. | TR-10/11 o N/A justificado. | Por ejecutar |
| 9 | Integridad y conclusión | Comprobar la cadena de identificadores, secuencia de tiempos, cambios antes/después, accesos y huecos. | Lista de faltantes, discrepancias e incidencia; sin completar con supuestos. | Por ejecutar |

Los eventos de excepción conservan su solicitud, actor, motivo y resolución: duplicados, cambios de precio, crédito, falta de stock, entrega parcial, descuadres de comprobante o reintentos. Si el comportamiento observado se aparta del esperado, se crea una incidencia relacionada con el caso de prueba y se conserva la evidencia del resultado real.

## Fuentes

| Documento | Aplicación en el plan |
| --- | --- |
| [Contexto de la empresa](../../arquitectura/base/contexto-empresa.md) | KeyFacil, canales y registros actuales. |
| [ADR-002](../../arquitectura/decisiones/ADR-002-version-y-edicion.md) | Selección de Odoo 18 Community. |
| [Vistas C4](../../arquitectura/vistas/consolidado-diagramas.md) | Límites del sistema, módulos, usuarios y objetos de ventas e inventario. |
| [Flujo O2C](../../procesos/o2c/flujo.md) y [flujo de inventario](../../procesos/inventario/flujo.md) | Estados y documentos de origen y destino. |
| [Riesgos y controles](../../arquitectura/base/riesgos-y-controles.md) y [backlog](../../producto/backlog.md) | Verificación de controles y actividades previstas. |
| [Modelo de autorización](../../arquitectura/seguridad/modelo-autorizacion.md) | Perfiles y acceso al rastro de auditoría. |
