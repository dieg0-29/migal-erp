# Datos

Esta carpeta documenta los datos que permiten integrar y reconstruir los procesos de Ferre & Inversiones MIGAL: qué significan, quién los mantiene, qué reglas de calidad cumplen, cómo se protegen y cómo se rastrea una operación entre el CRM, el ERP y KeyFacil.

## Contenido

| Carpeta / archivo | Contenido |
|---|---|
| [`plantilla-entidad.md`](plantilla-entidad.md) | Plantilla para documentar cada entidad de datos |
| [`maestros/`](maestros/) | Entidades estables compartidas: [clientes](maestros/clientes.md), [productos](maestros/productos.md), [precios](maestros/precios.md) y [proveedores](maestros/proveedores.md) |
| [`transaccionales/`](transaccionales/datos-transaccionales.md) | Objetos que nacen en cada operación: consulta, oportunidad, cotización, pedido, entrega, comprobante, pago y posventa |
| [`diccionario/`](diccionario/diccionario-datos.md) | Diccionario de datos: **única fuente** de definiciones de campos |
| [`calidad/`](calidad/reglas-calidad.md) | Reglas de calidad DQ-01 a DQ-12 |
| [`trazabilidad/`](trazabilidad/README.md) | Registro de identificadores, plan de trazabilidad y auditoría, y matriz de trazabilidad |
| [`privacidad/`](privacidad/tratamiento-datos.md) | Finalidad, minimización y uso operativo frente a promocional |
| [`pruebas/`](pruebas/README.md) | Catálogo sintético CRM usado en los casos de prueba |

## Convenciones

* **Identificadores y códigos:** todos los prefijos (CLI, OPP, COT…) y espacios de códigos (RN, CT, DQ, TR…) están en el [registro de identificadores](trazabilidad/identificadores-y-linaje.md). No se crea un código nuevo sin registrarlo allí.
* **Caso de ejemplo único:** los documentos usan los IDs del [catálogo sintético](pruebas/README.md): el caso normal es `OPP-SIM-001` / `COT-SIM-001-V01` y el caso de excepción es `OPP-SIM-002` / `COT-SIM-002-V02`.
* **Responsables:** se indican con los perfiles del [modelo de autorización](../arquitectura/seguridad/modelo-autorizacion.md). La custodia de los datos maestros corresponde a R-PRO.
* **Etiquetas de evidencia:**

| Etiqueta | Significado |
|---|---|
| `[E]` | Evidencia respaldada por una fuente del negocio |
| `[I]` | Interpretación razonada a partir de evidencia |
| `[S]` | Supuesto provisional pendiente de validación |
| `[ND]` | No determinado: no hay información suficiente |
| `AS-IS` / `TO-BE` | Situación actual / mejora propuesta |
| `[SIM]` | Dato ficticio, solo para pruebas |

## Reglas

- No subir credenciales, secretos ni datos personales reales.
- No presentar datos simulados como información real de la empresa; todo dato de prueba lleva el sufijo `-SIM` o la etiqueta `[SIM]`.
- Los cambios en maestros o reglas de calidad se revisan contra procesos, arquitectura y pruebas.
