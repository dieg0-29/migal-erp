# EVO-01: Arquitectura base — ERP

## 1. Metadatos

* **Fecha:** 17/10/2026
* **Versión:** 0.1
* **Autores:** César Emmerson Joaquín Palomino
* **Sistema incorporado:** ERP (Odoo 18 Community)
* **Sistemas existentes afectados:** Ninguno

## 2. Propósito

Establecer la base operativa de MIGAL: ventas, punto de venta, inventario y contabilidad básica en una sola plataforma, conviviendo con KeyFacil para la emisión de comprobantes.

## 3. Elementos que se agregan


| Elemento | Decisión | Respaldo |
|---|---|---|
| Plataforma | Odoo como ERP, elegido frente a StarSoft y Microsoft Dynamics 365 | [ADR-001](../decisiones/ADR-001-seleccion-erp.md) |
| Versión y edición | Odoo 18 Community, por presupuesto y ausencia de personal de TI | [ADR-002](../decisiones/ADR-002-version-y-edicion.md) |
| Contabilidad | Módulos de la comunidad (OCA / Odoo Mates) | [ADR-003](../decisiones/ADR-003-contabilidad.md) |
| Módulos | Ventas, Punto de Venta, Inventario y contabilidad básica; sin Compras | [Vistas C4](../vistas/consolidado-diagramas.md) |
| Sistemas externos | KeyFacil para comprobantes; WhatsApp como canal, sin automatizar | [Contexto de la empresa](../base/contexto-empresa.md) |

## 4. Historial de cambios

| Versión | Fecha | Autor | Cambio |
|---|---|---|---|
| 0.1 | 17/10/2026 | César Emmerson Joaquín Palomino | Versión inicial |
