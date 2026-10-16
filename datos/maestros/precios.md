# Referencias de precio y condiciones comerciales

**Estado:** propuesta conceptual; no establece una lista real ni una fórmula universal de MIGAL.

## Distinciones

| Concepto | Significado | Conservación |
|---|---|---|
| Costo/referencia de compra | Insumo para decisión del propietario | Procedencia y fecha cuando esté disponible; acceso según finalidad |
| Precio de referencia | Base utilizada al preparar una oferta | Producto, unidad, moneda, fecha/origen |
| Precio ofrecido | Importe comunicado por línea | Cotización y versión; no sobrescribir oferta anterior |
| Ajuste | Diferencia entre referencia y ofrecido | Motivo, autorizador y fecha si corresponde |
| Condición de vigencia | Circunstancia que requiere revisión | Texto comunicado y versión aplicable |

FN-01/FN-02 registran decisiones basadas en producto, costo reciente, competencia y operación. No existe un porcentaje máximo universal formalizado en las fuentes del repositorio. Antes del pago puede cambiar la propuesta si cambian costos; las condiciones concretas deben comunicarse y validarse.

## Flujo de actualización propuesto

1. Identificar referencia disponible, fecha, producto y unidad.
2. Propietario revisa su conveniencia para la operación.
3. Persona que cotiza conserva referencia y precio ofrecido por línea.
4. Si hay cambio relevante, emitir nueva versión y conservar anterior, motivo y decisión.
5. Diferenciar modificación de una oferta de mantenimiento del catálogo general.

La fuente de verdad definitiva del precio vigente y su mecanismo de mantenimiento están pendientes. No se presume sincronización con KeyFacil ni fórmula automática.

## Validación y ejemplo

En COT-SIM-002-V02 el fierro tiene referencia SIM S/ 40.50 y ofrecido S/ 40.10 por unidad. Con 60 unidades, los importes son S/ 2,430.00 y S/ 2,406.00; diferencia S/ 24.00. No determina descuentos reales ni tratamiento fiscal. Aceptación: valores, unidad, versión, motivo y autorizador se pueden reconstruir; las diferencias monetarias se comparan a dos decimales sin alterar precios almacenados silenciosamente.

Referencias: [decisiones](../../procesos/comercial-crm/decisiones-comerciales.md), [oportunidad/cotización](../../procesos/comercial-crm/lead-oportunidad-cotizacion.md), [calidad](../calidad/reglas-calidad.md), [fuentes](../../fuentes/fuentes-negocio.md).
