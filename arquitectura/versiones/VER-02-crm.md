# VER-02: Integración del CRM

## 1. Metadatos

* **Fecha:** 17/10/2026
* **Versión:** 0.1
* **Autores:** César Joaquín
* **Sistema incorporado:** CRM (Odoo 18 Community, misma instancia)
* **Sistemas existentes afectados:** ERP

## 2. Propósito

Recuperar el contexto comercial disperso en conversaciones, notas y memoria de los propietarios, e integrarlo al ERP existente mediante la frontera definida en [INT-01](../integraciones/INT-01-CRM-ERP.md).


## 3. Elementos que se mantienen

| Elemento | Observación |
|---|---|
| Odoo 18 Community | El CRM se incorpora en la misma instancia; no se reabre la elección de plataforma |
| KeyFacil como sistema externo | No se integra técnicamente con el CRM ni con el ERP |
| WhatsApp sin automatizar | Pasa a registrarse como canal en el CRM |
| Exclusión del módulo de Compras | Se mantiene |
| Supuesto de adopción por los propietarios | Se extiende al registro de consultas y cotizaciones |

## 4. Elementos que se agregan

| Elemento | Descripción | Respaldo |
|---|---|---|
| Módulo CRM | Leads, oportunidades, etapas, probabilidad, actividades y motivos de pérdida | [Escenario CRM](../../procesos/comercial-crm/escenario-crm.md) |
| Marketing / UTM | Campaña, fuente y medio de cada lead | [Cuenta, contacto y canales](../../procesos/comercial-crm/cuenta-contacto-canales.md) |
| Contactos | Cuenta (cliente u obra) y contactos (dueño, maestro, receptor) | [Cuenta, contacto y canales](../../procesos/comercial-crm/cuenta-contacto-canales.md) |
| Reglas y decisiones comerciales | Responsables y evidencia para descuento, disponibilidad y comprobante previsto | [Decisiones comerciales](../../procesos/comercial-crm/decisiones-comerciales.md) |
| Frontera CRM a ERP | La cotización aceptada pasa al ERP como pedido | [INT-01](../integraciones/INT-01-CRM-ERP.md), [ADR-004](../decisiones/ADR-004-odoo-community-fronteras-crm-erp.md) |

## 5. Ajustes en el ERP para la integración

| ID | Componente ERP | Antes | Después | Motivo de la integración | Documentos afectados | Estado |
|---|---|---|---|---|---|---|
| CA-01 | Vistas de arquitectura | Centradas en ventas e inventario | Incluyen el dominio CRM y su relación con Ventas | Representar la nueva frontera | [Vistas C4](../vistas/consolidado-diagramas.md) | Documentado |
| CA-02 | Ventas | Cotización creada directamente en Ventas | Cotización creada desde la oportunidad (`sale_crm`); el pedido confirmado inicia la ejecución en el ERP | Conservar el origen comercial del pedido | [INT-01](../integraciones/INT-01-CRM-ERP.md), [O2C](../../procesos/o2c/flujo.md) | Pendiente de prueba |
| CA-03 | Registros internos y KeyFacil | Documentos internos y comprobantes fiscales sin distinguir | KeyFacil conserva la emisión; Odoo mantiene el registro operativo y la referencia | Evitar duplicar la emisión fiscal | [ADR-004](../decisiones/ADR-004-odoo-community-fronteras-crm-erp.md), [Facturación](../../procesos/comercial-crm/facturacion.md) | Frontera documentada; flujo O2C por corregir |
| CA-04 | Abastecimiento | Solicitud de presupuesto automática en Compras ante falta de stock | No se presupone la solicitud automática; el abastecimiento se modela como proceso independiente del módulo | Coherencia con la exclusión de Compras | [O2C](../../procesos/o2c/flujo.md), [P2P](../../procesos/p2p/flujo.md), [Inventario](../../procesos/inventario/flujo.md) | Decisión pendiente |
| CA-05 | Precios | Precio modificable sin contexto | Se conserva versión, precio de referencia, precio ofrecido, motivo y autorizador | Trazabilidad de excepciones de precio originadas en el CRM | [Decisiones comerciales](../../procesos/comercial-crm/decisiones-comerciales.md) | Pendiente de prueba |
| CA-06 | Punto de Venta | Descuento de stock inmediato y al cierre descritos a la vez | Fijar una configuración y documentar el momento efectivo | Disponibilidad confiable para las promesas comerciales | [O2C](../../procesos/o2c/flujo.md), [Inventario](../../procesos/inventario/flujo.md) | Sin resolver; requiere prueba |
| CA-07 | Contabilidad | Contabilidad de terceros descrita como requisito universal | Precisar brecha entre módulo estándar y complemento | Delimitar qué registra el ERP frente a KeyFacil | [ADR-003](../decisiones/ADR-003-contabilidad.md) | Corrección pendiente del ADR |
| CA-08 | Datos de prueba | Sin guía común | Distinguir catálogos sintéticos, IDs de caso e IDs de sistema | Probar el recorrido CRM a ERP de forma reproducible | [Datos de prueba](../../datos/pruebas/README.md) | Guía incorporada; ejecución pendiente |

## 6. Decisiones pendientes

* Revisar [ADR-003](../decisiones/ADR-003-contabilidad.md) con su autora en lugar de crear otro ADR que lo reemplace.
* Evaluar nuevos ADR para abastecimiento sin Compras, modelo de almacenes y ubicaciones, y respaldo y recuperación del entorno.
* Determinar si la política del Punto de Venta y la responsabilidad sobre los datos maestros requieren ADR o bastan registros de configuración.

## 7. Historial de cambios

| Versión | Fecha | Autor | Cambio |
|---|---|---|---|
| 0.1 | 17/10/2026 | César Joaquín | Versión inicial |
