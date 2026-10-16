# Alcance del proyecto MIGAL

**Estado:** propuesta documental para revisión del equipo, 16/10/2026. Sustituye únicamente en esta copia de trabajo el contenido incompleto `f` recibido.

## Objetivo

Organizar procesos, datos, aplicaciones, controles y evidencia para reducir la fragmentación de información comercial y operativa de MIGAL. El repositorio acumula incrementos académicos; documentar una capacidad no implica que esté implementada.

## Corte por incremento

| Incremento | Incluido | Límite / condición |
|---|---|---|
| PC1 representada en el repositorio | Contexto, comparación ERP, ADR, C4 y flujos propuestos de ventas/inventario | Corregir contradicciones; no acredita despliegue |
| PC2 v2.1 declarada | Cuenta/contactos, obra/dirección, canales/fuentes, lead, oportunidad, cotización/versiones, decisiones de precio/promesa/comprobante previsto, caso normal y excepción | Termina antes de pedido confirmado; rúbrica original por cotejar |
| Extensión hacia EP | Integración de arquitectura, procesos y datos; preparación de pedido, inventario, facturación, cobro y posventa cuando lo exija el hito | Requisitos oficiales EP, responsables y evidencia aún por confirmar |
| Implementación posterior | Configuración y pruebas en instancia Odoo, operación y controles verificables | Requiere entorno, módulos y procedimientos documentados |

## Fuera de ejecución PC2

Creación/ejecución del pedido, reserva, abastecimiento, entrega, emisión fiscal, cobro y posventa; contratos técnicos, APIs, conectores con WhatsApp/KeyFacil y agentes comerciales. Los documentos de esos temas son contexto futuro, no demostraciones de cumplimiento actual.

## Límites de solución propuestos

- Odoo 18 Community es la plataforma propuesta en ADR-001/002; sus estados siguen Propuesto.
- CRM conserva contexto; Ventas e Inventario gestionarán ejecución cuando se incorporen.
- KeyFacil conserva emisión fiscal según ADR-004; no se presume integración automática.
- La necesidad de un complemento contable debe precisarse al revisar ADR-003.
- P2P puede modelarse aunque el módulo Compras no se implante en esta fase. La discrepancia sobre RFQ automática de O2C queda pendiente de resolución.
- Tienda y dos almacenes son puntos físicos; su representación lógica requiere decisión.

## Entregables y aceptación

| Entregable | Criterio propuesto |
|---|---|
| Escenario CRM y casos | Recorrido reconstruible hasta cotización; datos SIM y frontera explícita |
| Datos y fuentes | Definiciones coherentes, IDs relacionados y evidencia localizable o pendiente declarado |
| Controles | Responsable funcional, condición, evidencia y aplicabilidad por etapa |
| Arquitectura | Decisiones y vistas compatibles con procesos; limitaciones visibles |
| Pruebas | Esperado/obtenido separados; solo afirmar ejecución con evidencia |

## Responsabilidad y control de cambios

Producto prepara trazabilidad del alcance; Facilitación confirma reparto; cada área revisa sus artefactos. No se asignan tareas a personas sin confirmación. D09/D10 conservan a Luis como responsable y D05/D06/ADR-004 a Gabriel como autor. Los cambios relevantes se registran en changelog y evolución arquitectónica.

## Fuentes y pendientes

[Supuestos y vacíos](../../fuentes/supuestos-y-vacios.md), [fuentes de negocio](../../fuentes/fuentes-negocio.md), [escenario CRM](../../procesos/comercial-crm/escenario-crm.md). Pendientes: cotejar rúbrica PC2/EP, validar reglas con propietarios y resolver contradicciones de PC1 antes de declarar aceptación integral.
