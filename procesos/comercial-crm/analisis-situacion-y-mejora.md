# Análisis de la situación actual y mejora propuesta

**Empresa:** Ferre & Inversiones MIGAL  
**Curso:** GE703 — Sistemas Integrados Empresariales  
**Evaluación:** PC2 · Incremento comercial CRM  
**Autor:** César Joaquín  
**Versión:** v2.0  
**Etiquetas:** [H] hecho con fuente · [S] supuesto · [P] propuesta del equipo · [PEND] pendiente de confirmar con MIGAL · [SIM] caso simulado

## 1. Objetivo y alcance

Este documento describe cómo atiende MIGAL hoy a sus clientes antes de vender y propone una forma de ordenar esa atención con el módulo CRM de Odoo. Cubre la cuenta, el contacto, el canal, la fuente o campaña, las interacciones, el lead, la oportunidad (necesidad, probabilidad y competidores) y la cotización con su versión, precio, descuento y vigencia.

El análisis termina cuando la oportunidad se cierra como ganada o perdida. Lo que ocurre después (pedido, inventario, despacho, facturación, cobro y posventa) corresponde al ERP y queda fuera de PC2, igual que cualquier contrato técnico, evento o interfaz entre ambos sistemas. Que un cliente acepte una cotización es un resultado comercial; no significa que ya exista un pedido.

## 2. Situación actual (AS-IS)

- [H] MIGAL es una ferretería con una tienda, dos almacenes, dos dueños y dos empleados. Atiende a clientes frecuentes y a maestros de obra (PC1, sección 1).
- [H] Las consultas y pedidos llegan por mostrador, WhatsApp y llamadas a los dueños, sin un horario definido para los mensajes (PC1, sección 1; `arquitectura/base/contexto-empresa.md`).
- [H] Los precios, las compras de cada cliente y otros datos importantes dependen de la memoria de los dueños. El registro se apoya en notas físicas y en KeyFacil, que se usa de forma incompleta (PC1, sección 1).
- [H] PC1 no menciona ningún CRM ni un historial único de interacciones y cotizaciones.
- [PEND] No hay datos medidos sobre cuántas consultas llegan, cuánto se tarda en responder, cuántas cotizaciones se emiten, cuántas terminan en venta ni por qué se pierden las demás.
- [PEND] Falta confirmar con los dueños si alguien lleva hoy algún registro propio de cotizaciones o seguimientos.

Con esto se puede decir cómo se atiende, pero no cuánto se pierde. Por eso no se atribuye a MIGAL una tasa de pérdida ni un impacto económico.

## 3. El problema que se quiere resolver

[S] Lo más probable es que el problema sea la falta de un registro compartido de la atención comercial. Si la consulta, lo que pidió el cliente, la cotización enviada y el siguiente paso quedan repartidos entre chats, llamadas y la memoria de cada dueño, retomar un caso o saber en qué terminó resulta difícil, sobre todo cuando los dos dueños atienden a la vez.

Esto es una hipótesis de trabajo. Para confirmarla hace falta observar la atención, revisar una muestra autorizada de consultas y conversar con quienes las atienden.

## 4. Mejora propuesta (TO-BE)

[P] El flujo que se propone para el módulo CRM de Odoo es este:

1. Cada consulta se registra con su canal, la fuente o campaña si se conoce, y quién la atiende.
2. Antes de crear nada se busca si el cliente o contacto ya existe. Si existe se vincula; si no, se crea un registro mínimo.
3. Se anota la interacción y lo que el cliente necesita, con el detalle suficiente para que otra persona pueda retomarla.
4. Se crea el lead y, cuando hay una necesidad concreta, la oportunidad, con etapa, responsable, probabilidad (alta, media o baja) y competidores si el cliente los menciona. No se piden datos que el cliente no ha dado ni que la consulta no necesita.
5. Se registra la cotización con su versión, precios, descuento, vigencia y la fuente de los precios usados.
6. Si el cliente pide un precio especial, lo decide un propietario y queda anotado el motivo y la decisión (FN-01 y FN-02).
7. Ventas no promete disponibilidad ni plazos sin una confirmación de quien controla el stock.
8. Al enviar la cotización se registra la comunicación, la respuesta y la siguiente acción. Mientras no haya respuesta, la oportunidad sigue abierta con un responsable y una próxima acción.
9. La oportunidad se cierra como ganada o perdida; si se pierde, con su motivo.
10. Si se gana, se deja constancia del resultado y de la cotización aceptada para que el proceso posterior parta de ahí. El CRM no crea el pedido por sí solo.

## 5. Contexto comercial del cliente: qué se guarda y por qué

| Elemento | Para qué sirve | Actualización mínima | Observación |
|---|---|---|---|
| Cuenta | Identificar a la persona o empresa y juntar sus interacciones. | Nombre y los datos necesarios para distinguirla de otra. | [PEND] Acordar campos obligatorios para persona natural y para empresa. |
| Contacto | Saber con quién se habla y cómo retomar la conversación. | Nombre, relación con la cuenta y un medio de contacto. | Útil sobre todo con maestros de obra que compran para terceros. |
| Canal | Saber por dónde llegó la consulta. | Tienda, llamada, WhatsApp u otro. | [H] Son los canales descritos en PC1; su peso relativo no está medido. |
| Fuente o campaña | Saber cómo conoció el cliente a MIGAL. | La fuente que el cliente declara; si no la sabe, se anota "no informado". | No se inventan campañas. |
| Interacción | Conservar lo conversado y lo acordado. | Canal, resumen breve, responsable y siguiente acción. | Solo información comercial necesaria. |
| Consentimiento y preferencias | Respetar si el cliente autoriza el contacto y por qué medio. | La preferencia o autorización que el cliente exprese. | [PEND] MIGAL debe definir cómo la obtiene y la guarda. |
| Dirección | Apoyar una cotización cuando la ubicación importa (por ejemplo, la obra). | Solo la dirección que el caso necesite. | No se pide a todos los leads. |
| Oportunidad | Seguir una intención de compra concreta. | Necesidad, etapa, responsable, probabilidad y competidores si se conocen. | [S] Las etapas y criterios de calificación se validan con el equipo y con MIGAL. |
| Cotización | Conservar la propuesta que recibió el cliente. | Versión, precios, descuento, vigencia y fecha de envío. | No se fijan porcentajes ni vigencias que no tengan sustento. |

## 6. Frontera entre CRM y ERP

La frontera es de responsabilidades, no de interfaces. Aunque ambos módulos vivan en Odoo, cada uno responde por cosas distintas.

| Tema | Lo que conserva el CRM | Lo que compromete y ejecuta el ERP |
|---|---|---|
| Cliente | Cuenta, contactos, historial de interacciones, canal y fuente. | Los datos que el cliente necesita para comprar y pagar, cuando exista un pedido. |
| Precio | El precio y el descuento comunicados en cada versión de la cotización. | La lista de precios vigente y su mantenimiento. |
| Disponibilidad | Lo que se comunicó al cliente y quién lo confirmó. | El stock real y su reserva para un pedido. |
| Aceptación | El resultado comercial: oportunidad ganada o perdida y su motivo. | La creación del pedido y su ejecución (despacho, entrega). |
| Facturación | La condición que se le comunicó al cliente. | La emisión del comprobante, que hoy se hace en KeyFacil, y el cobro. |
| Posventa | Nada en PC2. | Fuera del alcance evaluado. |

Esta tabla no define mensajes, eventos ni controles técnicos entre los dos módulos; eso queda para una etapa posterior.

## 7. Decisiones comerciales y responsables

| Decisión | Responsable principal | Evidencia esperada | Observación |
|---|---|---|---|
| Descuento o precio especial | [H] Un propietario (FN-01, FN-02). | Motivo del pedido, precio antes y después, decisión del propietario y versión de cotización enviada. | No existe un porcentaje máximo formal, así que no se propone uno. |
| Disponibilidad o promesa al cliente | [P] Quien controla el stock del producto: un propietario o el empleado que este designe. Ventas comunica solo lo confirmado. | Confirmación identificable (mensaje o nota) de que hay stock y en qué condiciones. | [PEND] MIGAL debe validar quién cumple este rol. No se crea un cargo que la empresa no tiene. |
| Condición de facturación | [P] Quien emite los comprobantes en KeyFacil confirma el tipo de comprobante y la forma de pago antes de comunicarlos. | Condición comunicada al cliente y quién la confirmó. | El CRM solo registra la condición; emitir y cobrar es tarea del ERP. No se afirma que KeyFacil esté integrado con Odoo. |
| Vigencia de la cotización | Un propietario fija la regla; ventas la comunica. | La vigencia escrita en la versión enviada. | [H] No hay una vigencia fija establecida (FN-01, FN-02), por lo que no se propone un plazo. |

## 8. Casos de análisis

### 8.1 Caso normal [SIM]

Obra Alfa, un cliente simulado, consulta por materiales para una necesidad concreta. Ventas registra el canal, la fuente (si la conoce), el contacto, la necesidad y la interacción. Con el consentimiento del cliente para ser contactado, se califica la oportunidad y se registra una primera versión de la cotización con sus precios, descuento y vigencia. El cliente la acepta y la oportunidad se cierra como ganada.

- **Decisión:** seguir con la cotización ordinaria y registrar el resultado.
- **Responsable principal:** ventas.
- **Evidencia esperada:** registro de la consulta, de la necesidad, de la oportunidad, de la versión enviada y de la aceptación.
- **Impacto para el cliente:** no tiene que repetir lo que ya contó y puede retomar la conversación con las condiciones que recibió.
- **Respuesta propuesta:** confirmar el resultado comercial y dejar la referencia para el proceso posterior, sin decir que el pedido ya existe.

### 8.2 Excepción prioritaria [SIM]

Obra Alfa pide un descuento adicional que no está cubierto por ninguna regla.

- **Decisión:** ventas no concede el descuento por su cuenta y lo remite a un propietario.
- **Responsable principal:** el propietario decide; ventas documenta la solicitud y comunica la respuesta.
- **Evidencia esperada:** motivo de la solicitud, condiciones pedidas, decisión (aprobada o rechazada) y versión final de la cotización.
- **Impacto para el cliente:** recibe una respuesta clara y no una promesa de precio que MIGAL no ha autorizado.
- **Respuesta propuesta:** comunicar el precio aprobado o mantener la cotización original, y registrar la decisión y la comunicación.

Ambos casos son simulados para probar el diseño y no representan operaciones reales de MIGAL.

## 9. Indicadores propuestos

Ninguno tiene línea base todavía. Primero se mide y después se fijan metas.

| Indicador | Cómo se calcula | Qué hay que registrar |
|---|---|---|
| Tiempo de respuesta | Tiempo entre que llega la consulta y la primera respuesta. | Hora de recepción y de la primera respuesta. |
| Tiempo de cotización | Tiempo entre tener la información completa y enviar la cotización. | Hora de información completa y de envío. |
| Seguimientos a tiempo | Seguimientos hechos en el plazo acordado ÷ seguimientos que correspondían × 100. | Próxima acción, fecha objetivo y fecha real. |
| Conversión | Oportunidades ganadas ÷ oportunidades cerradas × 100. | Estado de cierre; las abiertas no cuentan. |
| Cotizaciones corregidas | Cotizaciones corregidas por error propio ÷ cotizaciones emitidas × 100. | Versiones y motivo de cada corrección. |
| Registros completos | Consultas con los campos mínimos ÷ consultas registradas × 100. | Campos mínimos acordados. |

## 10. Riesgos y controles

| Riesgo | Control propuesto | Estado |
|---|---|---|
| Registros duplicados o incompletos | Buscar antes de crear, pedir solo campos mínimos y asignar quién actualiza. | [S] Validar con quienes atienden. |
| Oportunidades sin seguimiento | Responsable y próxima acción en cada oportunidad abierta; revisión periódica. | [PEND] Definir cada cuánto. |
| Precios inconsistentes | Usar una fuente de precios identificada y registrar quién autoriza cada excepción. | [PEND] Confirmar la fuente de precios vigente. |
| Promesas de stock sin respaldo | Confirmación identificable antes de comunicar disponibilidad o plazos. | [PEND] Validar quién confirma. |
| Confundir CRM con ERP | Cerrar el CRM en el resultado comercial y tratar el pedido como proceso posterior. | Delimitado en la sección 6. |
| Dar por hecha una integración | Hablar de referencia o traspaso manual hasta que haya una prueba técnica. | PC2 no diseña interfaces. |
| Exceso de datos personales | Pedir lo necesario, limitar permisos y usar datos ficticios en pruebas y repositorio. | [PEND] Validar la política de privacidad. |
| Un riesgo que el CRM no resuelve | Si los precios siguen en la memoria de los dueños, el CRM registrará cotizaciones ordenadas pero con precios mal sustentados. | Requiere mantener una lista de precios, tarea del ERP. |
| Que no se use | Si el personal no registra las consultas, el historial quedará incompleto. | [S] PC1 ya asume que los dueños se adaptarán a registrar en Odoo. |

## 11. Costos y esfuerzo

No hay una estimación validada, por lo que no se presentan importes. Estos son los rubros que habría que evaluar antes de decidir.

| Rubro | Qué considerar | Estado |
|---|---|---|
| Licencia | [H] Odoo 18 Community es la edición elegida en PC1. | Community no implica costo cero: faltan hosting, configuración, soporte y mantenimiento. |
| Configuración del CRM | Etapas, campos, vistas, permisos y reportes que realmente se necesiten. | [S] Estimar cuando se validen los requisitos. Configurar antes de acordar las reglas automatizaría un proceso sin validar. |
| Depuración de datos | Revisar cuentas, contactos y duplicados. | [PEND] No se conoce el volumen ni la calidad actual. |
| Capacitación | Tiempo para enseñar a registrar consultas, cotizaciones y próximas acciones. | [PEND] Horas por confirmar. |
| Operación | Alojamiento, copias de seguridad, actualizaciones y accesos. | [PEND] PC1 señala que MIGAL no tiene personal de TI, por lo que habrá que ver quién lo asume. |
| Relación con facturación | Cómo se vincula la cotización aceptada con el comprobante en KeyFacil. | [H] PC1 mantiene KeyFacil y excluye la facturación directa; cualquier vínculo se evalúa después. |

Si no se adopta el CRM, la atención seguiría dependiendo de la memoria y de los chats de los dueños, con el costo de tiempo y de ventas sin seguimiento que eso implique, que hoy no está medido.

## 12. Conclusión

El CRM se justifica donde el problema es de registro: consultas que se pierden entre chats, cotizaciones que nadie puede reconstruir y excepciones de precio que no dejan rastro. No se justifica como solución a la falta de una lista de precios confiable ni al control del stock, que dependen del ERP y de la disciplina de los dueños.

El beneficio todavía no está demostrado. Para confirmarlo hay que levantar una línea base, validar con MIGAL las decisiones marcadas como pendientes y probar los casos de la sección 8. Pedido, facturación, entrega, cobro y posventa quedan fuera de este análisis.

## 13. Fuentes

- Documento PC1 del grupo (G1), sección 1: contexto y problema; sección 3: arquitectura; sección 4: decisión y límites.
- `arquitectura/base/contexto-empresa.md`: canales de atención y uso de KeyFacil.
- `README.md` y `procesos/README.md`: propósito y alcance del incremento.
- ADR-001, ADR-002 y ADR-003 (`arquitectura/decisiones/`): decisiones de arquitectura de PC1.
- FN-01 y FN-02: decisiones comerciales sobre descuentos y vigencia.
- GE703 PC2, Instrucciones y rúbrica: alcance y criterios de evaluación.
