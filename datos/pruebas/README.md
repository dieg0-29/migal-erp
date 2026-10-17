# Datos de prueba

## Catálogo sintético CRM

[catalogos-crm-sinteticos.xlsx](catalogos-crm-sinteticos.xlsx) contiene nombres, documentos, teléfonos, direcciones e importes **ficticios** `[SIM]` para ilustrar el proceso comercial antes del pedido. No es una base real ni una plantilla para importar a Odoo. Todos los casos de prueba del repositorio usan sus identificadores.

| Hojas | Uso |
|---|---|
| LEEME, Resumen | Convenciones y conteos |
| Catalogos_Apoyo | Vocabularios controlados |
| Clientes, Contactos, Direcciones_Obra | Relación comercial |
| Productos_Referencia | Materiales y unidades |
| Oportunidades | Necesidad, madurez, seguimiento y desenlace |
| Cotizaciones, Cotizaciones_Detalle | Versiones, líneas y precios |
| Decisiones_Comerciales | Motivos, responsables y condiciones |
| Trazabilidad_Fuentes | Procedencia de las afirmaciones |

Las definiciones de campos están en el [diccionario de datos](../diccionario-datos.md), no en el libro.

## Casos que lo usan

| Caso | Identificadores |
|---|---|
| [Caso normal](../../pruebas/casos/CP-01-caso-normal.md) (CP-01) | `CLI-SIM-001`, `CON-SIM-002`, `DIR-SIM-001`, `OPP-SIM-001`, `COT-SIM-001-V01` |
| [Caso de excepción](../../pruebas/casos/CP-02-caso-excepcion.md) (CP-02) | `CLI-SIM-002`, `CON-SIM-004`, `OPP-SIM-002`, `COT-SIM-002-V01` y `V02`, `DEC-SIM-001` |

Para pasos posteriores a la aceptación se usan los prefijos `PED-SIM`, `ENT-SIM`, `CPE-SIM` y `PAG-SIM` del [registro de identificadores](../trazabilidad/identificadores-y-linaje.md); aún no tienen filas en el libro.

## Uso

1. Trabajar sobre una copia si se van a cambiar datos.
2. Elegir un caso por ID, no por posición de fila.
3. Resolver cuenta, contacto, dirección, oportunidad, cotización y líneas.
4. Aplicar las [reglas de calidad](../reglas-calidad.md) y registrar esperado y obtenido.
5. Guardar evidencia sin datos privados; abrir el archivo no equivale a importar ni ejecutar.

## Limitaciones

* No hay hoja de interacciones; no se simula su presencia.
* La columna `origen` mezcla canal, fuente y campaña (ver pendientes del diccionario).
* Fechas, precios y resultados no describen operaciones reales.
