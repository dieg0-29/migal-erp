# Precios y condiciones comerciales

## 1. Metadatos

* **Fecha:** 17/10/2026
* **Versión:** 0.1
* **Autores:** Brenda Mirano
* **Sistema dueño:** ERP (lista de precios) y CRM (precio ofrecido por cotización)
* **Custodio:** R-PRO

## 2. Propósito

Distinguir el precio de lista del precio realmente ofrecido y conservar por qué cambió, sin establecer una lista real ni una fórmula universal de MIGAL. No existe un porcentaje máximo de descuento formalizado `[E]`.

## 3. Campos

| Concepto | Significado | Se conserva |
|---|---|---|
| Costo o referencia de compra | Insumo para la decisión del propietario | Procedencia y fecha; acceso según finalidad |
| Precio de referencia | Base para preparar una oferta | Producto, unidad, moneda, fecha y origen |
| Precio ofrecido | Importe comunicado por línea | Cotización y versión; no sobrescribe la oferta anterior |
| Ajuste | Diferencia entre referencia y ofrecido | Motivo, autorizador y fecha |
| Condición de vigencia | Circunstancia que obliga a revisar el precio | Texto comunicado y versión aplicable |

Definiciones completas en el [diccionario de datos](../diccionario-datos.md).

## 4. Reglas de calidad aplicables

* DQ-05 precio interpretable, DQ-06 cambio de precio reconstruible y DQ-07 versión no sobrescrita ([reglas de calidad](../reglas-calidad.md)).
* RN-03 precios de lista vigente, RN-04 versionado y EXC-01 excepción de descuento ([decisiones comerciales](../../procesos/comercial-crm/decisiones-comerciales.md)).

## 5. Mantenimiento

| Acción | Perfil | Condición |
|---|---|---|
| Actualizar la lista de precios | R-PRO | Con referencia, fecha, producto y unidad |
| Cotizar | R-ATN | Conserva precio de referencia y ofrecido por línea |
| Autorizar un ajuste | R-PRO | Otro propietario si el ajuste lo inició un propietario (SOD-01) |
| Cambio relevante | R-ATN | Nueva versión de la cotización; se conserva la anterior |

## 6. Ejemplo `[SIM]`

En `COT-SIM-002-V02` la barra de fierro (`PRD-SIM-002`) tiene precio de referencia S/ 40.50 y ofrecido S/ 40.10. Con 60 unidades, los importes son S/ 2,430.00 y S/ 2,406.00: diferencia S/ 24.00, autorizada por el dueño (`DEC-SIM-001`).

## 7. Pendientes

* Fuente de verdad del precio vigente y su mecanismo de mantenimiento.
* No se presume sincronización con KeyFacil ni fórmula automática.

## 8. Historial de cambios

| Versión | Fecha | Autor | Cambio |
|---|---|---|---|
| 0.1 | 17/10/2026 | Brenda Mirano | Versión inicial con la plantilla de entidad |

Referencias: [lead, oportunidad y cotización](../../procesos/comercial-crm/lead-oportunidad-cotizacion.md), [fuentes](../../fuentes/fuentes-negocio.md).
