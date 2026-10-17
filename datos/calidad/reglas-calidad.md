# Reglas de calidad de datos

**Estado:** controles propuestos para revisión; no resultados de pruebas ni restricciones técnicas instaladas. IDs `DQ-*` evitan reutilizar los RN/CT existentes del plan de trazabilidad.

| ID | Regla y etapa | Comprobación | Tratamiento si falla | Función responsable |
|---|---|---|---|---|
| DQ-01 | Identificadores únicos por entidad | Buscar repetidos no vacíos | Revisar identidad; no fusionar automáticamente | Datos |
| DQ-02 | Relaciones existentes | Contacto→cuenta, oportunidad→cuenta/contacto, cotización→oportunidad, detalle→cotización/producto | Resolver referencia o registrar pendiente | Datos/Atención |
| DQ-03 | Cuenta/contacto coherentes | Contacto corresponde a relación del caso | Validar interlocutor/representación | Atención |
| DQ-04 | Cantidad y unidad interpretables en cotización | Cantidad positiva y unidad del producto explícita | Corregir antes de comunicar | Quien cotiza |
| DQ-05 | Precio interpretable | Número positivo, moneda y unidad; formato monetario válido | Corregir dato/formato sin cambiar importe silenciosamente | Propietarios/Datos |
| DQ-06 | Cambio de precio reconstruible | Referencia, ofrecido, motivo, autorizador y versión | Mantener revisión pendiente | Propietarios |
| DQ-07 | Versión no sobrescrita | Familia/versión únicas; anterior conservada | Registrar revisión nueva | Quien cotiza |
| DQ-08 | Canal distinto de fuente | Presencial/WhatsApp/teléfono frente a referido/campaña | Separar conceptos y conservar origen | Atención |
| DQ-09 | Oportunidad abierta con seguimiento | Acción, fecha y responsable, o excepción motivada | Asignar seguimiento | Responsable comercial |
| DQ-10 | Desenlace comercial explicable | Motivo en pérdida/parcial y evidencia pertinente | No declarar cierre sin soporte | Responsable comercial |
| DQ-11 | Minimización y SIM | Ausencia de datos privados reales en casos académicos | Sustituir por sintéticos antes de publicar | Quien prepara evidencia |
| DQ-12 | Fechas y estados coherentes | Emisión anterior a revisión/aceptación; distinguir estado actual y desenlace | Revisar secuencia, no completar con supuestos | Atención/Validación |

## Ejecución y evidencia

Para cada revisión registrar regla, archivo/hoja/rango o ID, dato observado, esperado, resultado, revisor, fecha e incidencia. “No aplicable” necesita motivo; ausencia de evidencia no equivale a aprobado. Frecuencia propuesta: al preparar una versión de catálogo y antes de entregar un caso; periodicidad operativa por validar.

## Ejemplo de revisión

COT-SIM-001-V01 debe resolver OPP-SIM-001 y PRD-SIM-001/002/003; la suma de líneas SIM es S/ 5,000.00 sin agregar impuestos no definidos. El formato monetario del libro recibido requiere revisión: usar `"S/" #,##0.00`. Esta regla documenta la corrección necesaria; el libro no se modifica como parte del llenado de Markdown.

## Límites

Estas comprobaciones no acreditan importación, controles automáticos, validez tributaria ni stock real. Para fases posteriores agregar conciliación pedido–entrega–comprobante–pago y calidad de proveedores sin reutilizar IDs ambiguos.

Referencias: [diccionario](../diccionario/diccionario-datos.md), [plan de trazabilidad](../trazabilidad/plan-trazabilidad-auditoria.md), [privacidad](../privacidad/tratamiento-datos.md).
