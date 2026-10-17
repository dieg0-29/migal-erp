# Procesos

Esta carpeta modela los procesos de Ferre & Inversiones MIGAL: cómo fluye el valor de extremo a extremo, qué perfiles participan, qué reglas se aplican y qué evidencia permite reconstruir cada operación.

## Contenido

| Archivo / carpeta | Contenido |
|---|---|
| [`mapa-nivel-1/`](mapa-nivel-1/mapa-procesos.md) | Mapa general de procesos e índice de documentos por proceso |
| [`catalogo-reglas.md`](catalogo-reglas.md) | **Catálogo único** de reglas (RN), controles (CT) y excepciones (EXC) de todos los procesos |
| [`plantilla-proceso.md`](plantilla-proceso.md) | Plantilla para documentar un proceso |
| [`comercial-crm/`](comercial-crm/) | [Flujo comercial](comercial-crm/flujo-comercial.md) (consulta a cotización aceptada), [cuenta, contacto y canales](comercial-crm/cuenta-contacto-canales.md), [decisiones comerciales](comercial-crm/decisiones-comerciales.md) y [justificación del CRM](comercial-crm/justificacion-crm.md) |
| [`o2c/`](o2c/) | Order to Cash: [SIPOC](o2c/sipoc.md), [flujo](o2c/flujo.md), [pedido](o2c/pedido.md), [facturación](o2c/facturacion.md) e [indicadores](o2c/indicadores.md) |
| [`p2p/`](p2p/) | Procure to Pay: [SIPOC](p2p/sipoc.md), [flujo](p2p/flujo.md), [eventos y controles](p2p/eventos-controles.md) e [indicadores](p2p/indicadores.md) |
| [`inventario/`](inventario/flujo.md) | Movimientos, transferencias y ajustes por ubicación |

Los casos de prueba de estos procesos están en [`pruebas/casos/`](../pruebas/casos/), y las transiciones entre sistemas en [`arquitectura/integraciones/`](../arquitectura/integraciones/).

## Convenciones

* Cada proceso nuevo usa la [plantilla de proceso](plantilla-proceso.md).
* Los actores se indican con los perfiles del [modelo de autorización](../arquitectura/seguridad/modelo-autorizacion.md) (R-ATN, R-PRO, R-ALM, R-FAC); no se inventan cargos que MIGAL no tiene.
* Las reglas se citan con su código del [catálogo de reglas](catalogo-reglas.md); no se crean catálogos paralelos por proceso.
* Se separa el AS-IS del TO-BE y se usan las etiquetas de evidencia del [README de datos](../datos/README.md#convenciones).
* Ningún comportamiento de Odoo se describe como existente sin haberlo probado; lo no probado se marca `[S]` o "por validar".
