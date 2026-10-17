# Reglas de calidad de datos

## 1. Metadatos

* **Fecha:** 17/10/2026
* **Versión:** 0.1
* **Autores:** Brenda Mirano
* **Custodio:** R-PRO

## 2. Propósito

Definir las comprobaciones que hacen confiables los datos. Son controles propuestos, no restricciones instaladas en Odoo. Los códigos DQ son propios de este documento y no reemplazan las reglas RN ni los controles CT de las [decisiones comerciales](../../procesos/comercial-crm/decisiones-comerciales.md).

## 3. Reglas

| ID | Regla | Comprobación | Tratamiento si falla | Responsable |
|---|---|---|---|---|
| DQ-01 | Identificadores únicos por entidad | Buscar repetidos no vacíos | Revisar identidad; no fusionar automáticamente | R-PRO |
| DQ-02 | Relaciones existentes | Contacto a cuenta, oportunidad a cuenta y contacto, cotización a oportunidad, detalle a cotización y producto | Resolver la referencia o registrar pendiente | R-PRO / R-ATN |
| DQ-03 | Cuenta y contacto coherentes | El contacto corresponde a la relación del caso | Validar interlocutor y representación | R-ATN |
| DQ-04 | Cantidad y unidad interpretables | Cantidad positiva y unidad del producto explícita | Corregir antes de comunicar | R-ATN |
| DQ-05 | Precio interpretable | Número positivo con moneda y unidad, formato `"S/" #,##0.00` | Corregir el formato sin cambiar el importe | R-PRO |
| DQ-06 | Cambio de precio reconstruible | Referencia, ofrecido, motivo, autorizador y versión | Mantener revisión pendiente | R-PRO |
| DQ-07 | Versión no sobrescrita | Familia y versión únicas; anterior conservada | Registrar una revisión nueva | R-ATN |
| DQ-08 | Canal distinto de fuente | Presencial, WhatsApp o teléfono frente a referido o campaña | Separar conceptos y conservar el origen | R-ATN |
| DQ-09 | Oportunidad abierta con seguimiento | Acción, fecha y responsable, o excepción motivada | Asignar seguimiento | R-ATN |
| DQ-10 | Desenlace comercial explicable | Motivo en pérdida o ganancia parcial, con evidencia | No declarar cierre sin soporte | R-ATN |
| DQ-11 | Minimización y datos `[SIM]` | Sin datos privados reales en casos de prueba | Sustituir por sintéticos antes de publicar | R-PRO |
| DQ-12 | Fechas y estados coherentes | Emisión anterior a revisión y aceptación; estado actual distinto del desenlace | Revisar la secuencia sin completar con supuestos | R-ATN |

## 4. Ejecución y evidencia

Para cada revisión se registra regla, archivo, hoja, rango o ID, dato observado, esperado, resultado, revisor, fecha e incidencia. "No aplicable" requiere motivo; la ausencia de evidencia no equivale a aprobado. Se revisa al preparar una versión del catálogo y antes de entregar un caso; la periodicidad operativa está por validar.

## 5. Ejemplo `[SIM]`

`COT-SIM-001-V01` debe resolver `OPP-SIM-001` y los productos `PRD-SIM-001`, `PRD-SIM-002` y `PRD-SIM-003`. La suma de líneas es S/ 5,120.00 (100 × 31.00 + 40 × 40.50 + 20 × 20.00), sin impuestos.

## 6. Pendientes

* Agregar conciliación pedido–entrega–comprobante–pago y calidad de proveedores al configurar el ERP.
* Estas comprobaciones no acreditan importación, controles automáticos, validez tributaria ni stock real.

## 7. Historial de cambios

| Versión | Fecha | Autor | Cambio |
|---|---|---|---|
| 0.1 | 17/10/2026 | Brenda Mirano | Versión inicial con responsables por perfil |

Referencias: [diccionario](../diccionario/diccionario-datos.md), [plan de trazabilidad](../trazabilidad/plan-trazabilidad-auditoria.md), [privacidad](../privacidad/tratamiento-datos.md).
