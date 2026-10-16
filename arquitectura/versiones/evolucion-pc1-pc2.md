# D13. Evolución del proyecto: PC1 y PC2

**Empresa:** Ferre & Inversiones MIGAL  
**Curso:** GE703 — Sistemas Integrados Empresariales  
**Evaluación:** PC2 · Incremento comercial CRM  
**Autor:** Joaquín Palomino, César Emmerson  
**Versión del incremento:** v2.0 (PC1 fue v1.0)  
**Etiquetas:** [H] hecho con fuente · [S] supuesto · [P] propuesta del equipo · [PEND] pendiente de confirmar

## 1. Cómo se clasifican los cambios

Cada decisión de PC1 se compara con lo que PC2 hace con ella y se clasifica así:

- **Se mantiene:** sigue vigente sin cambios.
- **Se modifica:** cambia para reflejar el nuevo alcance comercial.
- **Nueva:** aparece en PC2 y no existía en PC1.
- **Fuera de alcance:** PC2 no la desarrolla.

Que una decisión esté documentada no significa que Odoo esté instalado ni que las integraciones funcionen. PC2 sigue siendo un trabajo de análisis y diseño.

## 2. Matriz de evolución PC1–PC2

| Tema | Estado | Qué decía PC1 | Qué pasa en PC2 | Dónde se refleja |
|---|---|---|---|---|
| Elección de Odoo como ERP (ADR-001) | Se mantiene | Se compararon StarSoft, Odoo 18 y Dynamics 365 y se eligió Odoo (PC1, secciones 2 y 4). | No se reabre la elección. El CRM se plantea dentro de Odoo. | D04, secciones 1 y 6 |
| Odoo 18 Community (ADR-002) | Se mantiene | Se adopta la edición Community por presupuesto y falta de personal de TI (PC1, secciones 2 y 4). | Se conserva. [S] El módulo CRM está disponible en Community; se confirma al configurarlo. | D04, sección 11 |
| Contabilidad comunitaria (ADR-003) | Se mantiene | El módulo contable oficial es de pago; se buscaron alternativas de la comunidad (PC1, uso de IA y fuentes). | No se toca; la contabilidad queda fuera de PC2. | — |
| KeyFacil para facturación | Se mantiene | Se conserva la integración actual con KeyFacil y se excluye la facturación directa desde Odoo (PC1, secciones 3 y 4). | Se conserva como herramienta externa. No se afirma que esté integrada con el CRM ni con Odoo. | D04, secciones 6 y 11 |
| WhatsApp como canal | Se mantiene | Se mantienen las comunicaciones por WhatsApp y se excluye su automatización (PC1, secciones 3 y 4). | Es uno de los canales que el CRM registra, sin automatizarlo. | D04, sección 5 |
| Límites de PC1 (sin módulo de Compras) | Se mantiene | El alcance inicial excluye Compras (PC1, sección 4). | Se respeta. | — |
| Backlog de PC1 (catálogo, inventario y ventas) | Se mantiene | Catálogo, inventario con Kardex y flujo de ventas mayoristas y POS (PC1, sección 4). | PC2 no lo avanza; solo añade el tramo comercial previo al pedido. | — |
| Supuesto de adopción por los dueños | Se mantiene | Se asume que los dueños se adaptarán a registrar sus transacciones en Odoo (PC1, límites). | Se aplica también al registro de consultas y cotizaciones. | D04, sección 10 |
| Vistas C4 de contexto y contenedores | Se modifica | PC1 mostraba usuarios, Odoo con Ventas, POS e Inventario, PostgreSQL, WhatsApp y KeyFacil (PC1, sección 3). | Se agrega el módulo CRM y se muestra su relación con ventas. | `arquitectura/vistas/c4/` |
| Escenario CRM previo al pedido | Nueva | PC1 no incluía cuenta, contacto, lead, oportunidad ni cotización. | Se agrega el escenario completo hasta el cierre comercial. | D04, secciones 4 y 5 |
| Frontera CRM–ERP | Nueva | PC1 trataba el sistema como un conjunto sin separar el CRM. | Se define qué conserva el CRM y qué compromete y ejecuta el ERP, de forma conceptual. | D04, sección 6 |
| Decisiones comerciales | Nueva | No estaban definidas. | Se asignan responsables y evidencia para descuento, disponibilidad y facturación. | D04, sección 7 |
| Caso normal y excepción | Nueva | No existían. | Se agregan dos casos simulados. | D04, sección 8 |
| Indicadores comerciales | Nueva | No existían. | Se proponen seis indicadores, aún sin línea base. | D04, sección 9 |
| Contrato técnico, eventos e interfaces CRM–ERP | Fuera de alcance | No estaba en PC1. | PC2 no lo desarrolla. | — |
| Pedido, facturación, entrega y posventa | Fuera de alcance | Solo se esbozan en el backlog de PC1. | PC2 llega hasta el resultado de la cotización. | — |

## 3. Resumen del incremento

PC2 mantiene todas las decisiones de arquitectura de PC1 y añade encima un escenario comercial de CRM: cómo se registra a un cliente, lo que consulta, la oportunidad que genera y la cotización que recibe, hasta que la oportunidad se gana o se pierde. También deja clara la frontera entre lo que conserva el CRM y lo que corresponde al ERP.

Lo único que cambia de la arquitectura de PC1 son las vistas C4, que ahora incluyen el módulo CRM.

## 4. Evidencias

| Evidencia | Para qué sirve |
|---|---|
| Documento PC1 del grupo (G1) | Confirmar lo que ya estaba decidido. |
| `arquitectura/decisiones/` (ADR-001, ADR-002, ADR-003) | Respaldar las decisiones que se mantienen. |
| `arquitectura/base/contexto-empresa.md` | Respaldar el contexto de KeyFacil y los canales. |
| `arquitectura/vistas/c4/` | Comparar las vistas antes y después del CRM. |
| `procesos/comercial-crm/` | Respaldar el escenario comercial nuevo. |

## 5. Fuentes

- Documento PC1 del grupo (G1): secciones 1 a 4 y declaración de límites.
- `arquitectura/base/contexto-empresa.md`.
- `arquitectura/decisiones/ADR-001-seleccion-erp.md`, `ADR-002-version-y-edicion.md` y ADR-003.
- GE703 PC2, Instrucciones y rúbrica.
