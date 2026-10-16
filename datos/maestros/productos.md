# Maestro conceptual de productos

**Estado:** catálogo propuesto. PC2 utiliza referencias sintéticas para cotizar; carga productiva pendiente.

## Definición y campos

| Campo | Uso | Regla propuesta |
|---|---|---|
| id_producto | Identidad estable | Único; no reciclar para otro material |
| descripcion | Selección comprensible | Incluir características que distingan variantes |
| marca / presentación | Evitar equivalencias falsas | Solo cuando corresponda; validar variantes |
| unidad_medida | Interpretar cantidad y precio | Obligatoria en cotización; unidad reconocible |
| categoria | Agrupación comercial | Vocabulario controlado |
| estado | Habilitar uso vigente | Activo/inactivo; conservar referencias históricas |
| nota / origen | SIM o procedencia del registro | No presentar catálogo sintético como inventario real |

Stock, costo y precio ofrecido no son la misma información que identidad de producto. La cotización conserva su precio por línea; no debe cambiar retroactivamente al modificar el catálogo.

## Mantenimiento y controles

Propietarios validan identidad comercial y unidades; el responsable funcional de datos prepara el registro. Buscar variantes antes de alta, revisar descripción/presentación/unidad y documentar sustituciones. No convertir automáticamente bolsa, unidad, rollo, galón o m3 sin equivalencia validada. Evitar texto libre cuando existe el artículo correcto; si falta, registrar solicitud de alta.

## Ejemplo

PRD-SIM-001: cemento, bolsa; PRD-SIM-002: fierro, unidad; PRD-SIM-005: arena gruesa, m3. Son ejemplos académicos y no determinan códigos, marcas ni unidades del negocio real.

## Futuro y validación

Al implantar Inventario se definirá tipo de producto, control de existencias, ubicaciones, costo y valoración. No deducir esas opciones del catálogo CRM. Aceptación: cada línea cotizada resuelve un producto activo y una unidad clara; variantes y conversiones quedan revisadas.

Referencias: [diccionario](../diccionario/diccionario-datos.md), [calidad](../calidad/reglas-calidad.md), [catálogo sintético](../pruebas/README.md), [fuentes](../../fuentes/fuentes-negocio.md).
