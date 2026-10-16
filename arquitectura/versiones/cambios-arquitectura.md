# Evolución de la arquitectura

**Estado:** registro documental propuesto al 16/10/2026. No es historial Git ni acta de aceptación.

## Cortes documentales

| Corte | Contenido | Evidencia y condición |
|---|---|---|
| Base PC1 representada en la copia | Selección ERP, versión, contabilidad, C4 y flujos ventas/inventario | ADR-001/002/003 y vistas; ADR en estado Propuesto |
| Incremento PC2 declarado | Cuenta/contactos, lead, oportunidad, cotización y decisiones comerciales | Documentos CRM y catálogos sintéticos; no acredita ejecución en Odoo |
| Extensión integrada | Pedido, inventario, comprobante, cobro y posventa | D05/D06 y partes futuras de D09/D10; por validar contra requisitos EP |

## Cambios conceptuales a consolidar

| ID | Antes o problema detectado | Propuesta vigente en este paquete | Artefactos afectados | Estado |
|---|---|---|---|---|
| CAM-01 | Vistas centradas en venta e inventario | Incorporar contexto CRM previo al pedido | Escenario CRM, C4, backlog | Documentado; C4 pendiente de revisión |
| CAM-02 | Documentos internos y fiscales confundidos | KeyFacil conserva emisión; Odoo mantiene registro operativo | O2C, ADR-004, facturación | Frontera documentada; flujo PC1 por corregir |
| CAM-03 | Compras automática frente a recepción manual | No presuponer RFQ automática; modelar P2P independiente del módulo | O2C, P2P, inventario, backlog | Diseño P2P propuesto; decisión técnica pendiente |
| CAM-04 | Precio modificado sin contexto | Conservar versión, referencia, ofrecido, motivo y autorización | CRM, maestros, D09/D10 | Regla propuesta; prueba pendiente |
| CAM-05 | Stock POS inmediato y al cierre como reglas simultáneas | Fijar una configuración y documentar el momento efectivo | C4, O2C, inventario | No resuelto; requiere prueba |
| CAM-06 | Contabilidad de terceros descrita como requisito universal | Precisar brecha estándar/complemento y configuración contable | ADR-003, backlog, flujos | Corrección pendiente del ADR existente |
| CAM-07 | Datos de prueba y operación sin guía común | Distinguir catálogos sintéticos, IDs de caso e IDs de sistema | Datos y pruebas | Guía documental incorporada; ejecución pendiente |
| CAM-08 | Controles ampliados sin corte académico | Separar PC2, futuro y condicional | D09/D10 y alcance | Corte propuesto; matrices existentes por revisar con Luis |

## Decisiones por formalizar o revisar

- Revisar ADR-003 con su autora; no crear otro ADR para ocultar su corrección.
- Reutilizar ADR-004 para convivencia con KeyFacil; precisar procedimiento y referencia cuando avance la ejecución.
- Evaluar nuevos ADR para abastecimiento sin Compras, topología de inventario y despliegue/recuperación.
- Determinar si la política POS y autoridad de maestros requieren ADR o bastan registros de configuración.

No se asignan números nuevos sin revisar las ramas activas. Una propuesta pasa a aceptada solo con evidencia de revisión y decisión del equipo.

## Registro de futuras modificaciones

Cada cambio incorporará fecha, motivo, documentos afectados, ADR relacionado, revisión y validación. Los renders se actualizarán junto con sus fuentes. El [changelog](../../CHANGELOG.md) resume incorporaciones; este registro explica su efecto arquitectónico.
