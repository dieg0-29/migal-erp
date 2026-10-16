# Datos de prueba CRM

**Archivo recibido:** [MIGAL_PC2_Catalogos_CRM_sinteticosxlsx.xlsx](MIGAL_PC2_Catalogos_CRM_sinteticosxlsx.xlsx). Se conserva su nombre y contenido para no romper referencias ni alterar evidencia de origen.

## Naturaleza y alcance

Libro académico con nombres, referencias e importes sintéticos. Representa conceptos CRM previos al pedido, no una base productiva ni plantilla lista para importar a Odoo. Cuenta/contacto, obra, productos de referencia, oportunidad y cotización permiten ilustrar seguimiento y decisiones. Los resultados comerciales registrados pueden representar desenlaces posteriores, no ejecución probada en PC2.

## Contenido

| Hojas | Uso |
|---|---|
| LEEME, Resumen | Convenciones y conteos del caso |
| Diccionario_CRM, Catalogos_Apoyo | Definiciones y vocabularios propuestos |
| Clientes, Contactos, Direcciones_Obra | Contexto de relación comercial |
| Productos_Referencia | Materiales/unidades ficticios |
| Oportunidades | Necesidad, madurez, seguimiento y desenlace |
| Cotizaciones, Cotizaciones_Detalle | Versiones, líneas y valores SIM |
| Decisiones_Comerciales | Motivos, responsables y condiciones |
| Trazabilidad_Fuentes | Procedencia conceptual y referencias del negocio |

## Uso reproducible

1. Conservar el libro original y trabajar sobre una copia si se autorizan cambios.
2. Elegir un caso por ID, no por posición de fila.
3. Resolver cuenta, contacto, dirección, oportunidad, cotización y líneas.
4. Revisar las [reglas de calidad](../calidad/reglas-calidad.md) y registrar esperado/obtenido.
5. Guardar evidencia sin datos privados; no afirmar importación o ejecución por abrir el archivo.

El [caso normal](../../procesos/comercial-crm/caso-normal.md) utiliza CLI-SIM-001/OPP-SIM-001/COT-SIM-001-V01. La negociación de competencia del libro está en COT-SIM-002-V02. El caso de excepción Markdown recibido usa otra variante y debe conciliarse o declararse independiente.

## Limitaciones pendientes

- El formato `S/ #,##0.00` debe corregirse a `"S/" #,##0.00` y verificarse visualmente en Excel; los valores recibidos son numéricos.
- No existe hoja de interacciones ni correlación técnica; no simular su presencia.
- Separar canal y fuente al consolidar el modelo; `origen` mezcla conceptos.
- Las fechas, precios y resultados no describen operaciones reales.

La validación de este paquete comprueba documentación y referencias, no recalcula ni altera el libro. Véanse [diccionario](../diccionario/diccionario-datos.md) y [fuentes](../../fuentes/fuentes-negocio.md).
