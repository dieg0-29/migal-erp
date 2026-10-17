# Productos

## 1. Metadatos

* **Fecha:** 17/10/2026
* **Versión:** 0.1
* **Autores:** Brenda Mirano
* **Sistema dueño:** ERP (catálogo consultado por el CRM)
* **Custodio:** R-PRO

## 2. Propósito

Identificar cada material con una unidad clara para cotizar sin ambigüedad. Stock, costo y precio ofrecido no forman parte de la identidad del producto; la cotización conserva su precio por línea y no cambia si se modifica el catálogo.

## 3. Campos

| Campo | Uso | Obligatorio |
|---|---|---|
| id_producto | Identidad estable; no se recicla para otro material | Sí |
| descripcion | Selección comprensible; distingue variantes | Sí |
| marca / presentación | Evitar equivalencias falsas | Cuando corresponda |
| unidad_medida | Interpretar cantidad y precio | Sí, en cotización |
| categoria | Agrupación comercial con vocabulario controlado | Sí |
| estado | Activo o inactivo; conserva referencias históricas | Sí |
| nota / origen | Indica si es `[SIM]` o su procedencia | Sí |

Definiciones completas en el [diccionario de datos](../diccionario/diccionario-datos.md).

## 4. Reglas de calidad aplicables

* DQ-01 identificadores únicos y DQ-04 cantidad y unidad interpretables ([reglas de calidad](../calidad/reglas-calidad.md)).
* No convertir automáticamente bolsa, unidad, rollo, galón o m3 sin una equivalencia validada.

## 5. Mantenimiento

| Acción | Perfil | Condición |
|---|---|---|
| Solicitud de alta | R-ATN | Cuando falta el artículo; no usar texto libre si existe el producto |
| Alta y modificación | R-PRO | Buscar variantes y revisar descripción, presentación y unidad |
| Desactivación | R-PRO | Documentar sustituciones |

## 6. Ejemplo `[SIM]`

`PRD-SIM-001`: cemento Portland, bolsa de 42.5 kg; `PRD-SIM-002`: barra corrugada de 1/2 pulg x 9 m, unidad; `PRD-SIM-005`: arena gruesa, m3. No determinan códigos, marcas ni unidades reales de MIGAL.

## 7. Pendientes

* Al configurar Inventario se definirán tipo de producto, control de existencias, ubicaciones, costo y valoración; no se deducen del catálogo CRM.
* Carga del catálogo real.

## 8. Historial de cambios

| Versión | Fecha | Autor | Cambio |
|---|---|---|---|
| 0.1 | 17/10/2026 | Brenda Mirano | Versión inicial con la plantilla de entidad |

Referencias: [catálogo sintético](../pruebas/README.md), [fuentes](../../fuentes/fuentes-negocio.md).
