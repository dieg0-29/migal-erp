# Criterios de aceptación del incremento CRM

**Curso:** GE703 — Sistemas Integrados Empresariales · Grupo 1
**Empresa:** Ferre & Inversiones MIGAL
**Base de evaluación:** instrucciones y rúbrica PC2, 2026-2 (20 puntos)

## Objeto y límites

Los siguientes criterios permiten revisar de forma reproducible el incremento comercial desarrollado en PC2. Se trata de **aceptación documental y académica**, no de pruebas de integración ni de certificación de una instancia Odoo. La revisión se concentra en cuenta, contacto, canal, campaña o fuente, interacción, lead, oportunidad y cotización; además, exige explicar de manera conceptual la frontera entre CRM y ERP.

Quedan fuera del alcance evaluable la creación o ejecución del pedido, la facturación, la entrega, la posventa, la implementación de interfaces, los eventos técnicos, los mecanismos de control de acceso y la trazabilidad operativa. Esos asuntos pueden mantenerse como continuidad del proyecto acumulativo, sin presentarse como cumplimiento de PC2.

## Matriz de criterios de aceptación

| ID | Criterio de la rúbrica | Puntos | Condición de aceptación observable | Evidencia de consulta |
| --- | --- | ---: | --- | --- |
| AC-01 | Modelo CRM y escenario comercial | 4 | El escenario relaciona cuenta, contacto, canal, campaña o fuente, interacción y actividades; modela lead y oportunidad con necesidad, probabilidad y competidores, y cotización con versión, precio, descuento y vigencia antes de confirmar el pedido. | `procesos/comercial-crm/flujo-comercial.md`, `procesos/comercial-crm/cuenta-contacto-canales.md` y `procesos/comercial-crm/flujo-comercial.md`. |
| AC-02 | Decisiones y responsabilidades | 4 | Para el descuento excepcional, la disponibilidad/promesa y la condición de facturación se distingue quién decide, cuál es el criterio y qué evidencia respalda la decisión. No se atribuyen al negocio umbrales ni plazos no confirmados. | `procesos/comercial-crm/decisiones-comerciales.md` y las fuentes de respaldo que el equipo valide. |
| AC-03 | Frontera CRM–ERP y alcance | 3 | Se explica qué conserva el CRM —contexto e intención comercial— y qué compromete o ejecuta el ERP una vez confirmada la operación, sin especificar contratos API, eventos ni automatizaciones fuera de alcance. | `arquitectura/integraciones/INT-01-CRM-ERP.md`, vistas de arquitectura C4 pertinentes. |
| AC-04 | Evidencia y caso de análisis | 3 | Se presenta un caso normal y una excepción prioritaria; ambos identifican decisión, responsable, evidencia esperada, impacto para el cliente y respuesta propuesta. Los datos simulados se distinguen de hechos del negocio. | `pruebas/casos/CP-01-caso-normal.md`, `pruebas/casos/CP-02-caso-excepcion.md`, presentación e informe grupal. |
| AC-05 | Argumentación y exposición | 3 | Un único integrante asignado expone durante un máximo de diez minutos y puede defender el escenario, las decisiones, las fuentes y los límites del alcance hasta la diapositiva 12. | Presentación, guion de exposición y designación del expositor. |
| AC-06 | Trabajo y participación | 2 | Los roles y aportes son identificables, equilibrados y verificables mediante contribuciones, revisiones, artefactos y registros de coordinación. | `README.md`, historial Git, revisiones y tabla de aportes en el informe grupal. |
| AC-07 | Ética y propiedad intelectual | 1 | El trabajo atribuye fuentes y licencias, declara propósito y límites de IA, muestra revisión humana y respeta la privacidad; los ejemplos no exponen datos reales no autorizados. | `fuentes/bibliografia.md`, `fuentes/licencias.md`, `fuentes/uso-ia.md`, documentación de privacidad y tabla de fuentes del informe. |

**Total de la rúbrica: 20 puntos.** La matriz define cómo revisar el cumplimiento documental; la calificación corresponde exclusivamente al docente.

## Comprobaciones para aceptar el paquete

| Código | Comprobación | Evidencia admisible |
| --- | --- | --- |
| CV-01 | Identificar grupo, empresa, integrantes, un único expositor, versión del incremento y proceso comercial analizado. | Portada e índice de la versión presentada. |
| CV-02 | Mantener el escenario hasta antes del pedido confirmado y respetar el corte de la diapositiva 12 de la sesión 6. | Lectura cruzada del escenario, las decisiones, los casos y la presentación. |
| CV-03 | Vincular cada decisión relevante con la fuente, sección o referencia consultada y su fecha de acceso. | Fuentes autorizadas, documentos versionados y bibliografía. |
| CV-04 | Distinguir evidencia, interpretación, supuesto, vacío de información y datos simulados. | Marcadores, notas metodológicas o explicación de cada artefacto. |
| CV-05 | Hacer verificables los responsables y aportes del equipo, sin atribuir al negocio reglas o cargos no confirmados. | Artefactos, revisiones, registros de coordinación y tabla de aportes del informe. |
| CV-06 | No presentar interfaces técnicas, controles de acceso, trazabilidad técnica, pedido, facturación, entrega ni posventa como requisitos evaluables de PC2. | Alcance declarado en los artefactos y presentación. |
| CV-07 | Declarar fuentes, licencias, propósito y límites del uso de IA, privacidad y validación humana. | Documentos de `fuentes/` y revisión del paquete. |
## Procedimiento de comprobación

Para cada CA y CV, el revisor identifica el documento y su versión, examina la evidencia disponible y registra el resultado: **cumple**, **cumple parcialmente**, **no cumple** o **no verificable**. Toda observación se vincula al archivo afectado y a la acción necesaria para corregirla. Una carpeta existente o un nombre de archivo, por sí solos, no prueban que un criterio esté cumplido.

Si una evidencia está aún fuera del repositorio, puede revisarse como archivo adjunto del grupo, identificando responsable y versión; su existencia no debe inferirse únicamente del plan de reparto. La revisión evita convertir un comportamiento esperado en una prueba efectivamente ejecutada.

## Documentos de referencia

- UNI-FIIS, GE703, *PC2 — Instrucciones y rúbrica*, 2026-2, pp. 1–2.
- Grupo 1, *PC2 — Plan de cierre y paquete de evidencias*, 16/10/2026, apartados 1, 4, 5 y 6.
- Grupo 1, [repositorio `migal-erp`](https://github.com/dieg0-29/migal-erp), especialmente [`procesos/comercial-crm/`](https://github.com/dieg0-29/migal-erp/tree/main/procesos/comercial-crm), [`fuentes/`](https://github.com/dieg0-29/migal-erp/tree/main/fuentes) y [`pruebas/`](https://github.com/dieg0-29/migal-erp/tree/main/pruebas).
