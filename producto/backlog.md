# Backlog del producto

## 1. Metadatos

* **Fecha:** 17/10/2026
* **Versión:** 0.1
* **Autores:** Diego Pinedo

## 2. Convenciones

* Cada historia (HU) indica el perfil del [modelo de autorización](../arquitectura/seguridad/modelo-autorizacion.md) y las reglas del [catálogo](../procesos/catalogo-reglas.md) que implementa.
* Una tarea marcada `[x]` está documentada; su configuración en Odoo solo se da por hecha con un caso de prueba ejecutado en [`pruebas/`](../pruebas/README.md).

## Épica 1: Modelado de arquitectura y procesos

* [x] Documentar la arquitectura C4 (contexto, contenedores y componentes): [vistas](../arquitectura/vistas/consolidado-diagramas.md).
* [x] Registrar las decisiones de plataforma, versión, contabilidad y fronteras: [ADR-001 a ADR-004](../arquitectura/decisiones/).
* [x] Modelar los procesos TO-BE comercial, O2C, P2P e inventario: [procesos](../procesos/README.md).
* [x] Definir la integración CRM a ERP: [INT-01](../arquitectura/integraciones/INT-01-CRM-ERP.md).

## Épica 2: Entorno base

* [x] Configurar el repositorio, la estructura de carpetas y las convenciones ([CONTRIBUTING](../CONTRIBUTING.md)).
* [ ] Decidir el alojamiento, el respaldo y el responsable técnico (R-TEC) del entorno (ADR pendiente).
* [ ] Instalar Odoo 18 Community y su base de datos PostgreSQL.

## Épica 3: Inventario

* `HU-01:` **Recepción y ajustes sin módulo de Compras.** Como personal de almacén (R-ALM), quiero registrar la cantidad realmente recibida y reportar diferencias, para que el stock refleje lo físico; los ajustes los autoriza un propietario (RN-19, RN-21, SOD-03).
* [ ] Configurar Tienda, Almacén 1 y Almacén 2 como almacenes o ubicaciones.
* [ ] Cargar el catálogo de productos con sus unidades de medida ([productos](../datos/maestros/productos.md)).

## Épica 4: Gestión comercial (CRM)

* `HU-05:` **Registro de consultas sin duplicados.** Como trabajador (R-ATN), quiero buscar el contacto existente antes de crear un lead, para no duplicar clientes (RN-01).
* `HU-06:` **Seguimiento de oportunidades.** Como trabajador (R-ATN), quiero registrar probabilidad, competencia y próxima acción, para que ninguna oportunidad quede sin seguimiento (RN-02).
* `HU-07:` **Cotización versionada.** Como trabajador (R-ATN), quiero emitir cotizaciones con precios de la lista vigente y conservar cada versión (RN-03, RN-04).
* `HU-08:` **Excepción de precio autorizada.** Como propietario (R-PRO), quiero aprobar un ajuste de precio dejando motivo y autorización en una nueva versión (EXC-01, SOD-01).
* [ ] Configurar etapas del CRM, fuentes, medios y motivos de pérdida.
* [ ] Ejecutar [CP-01](../pruebas/casos/CP-01-caso-normal.md) y [CP-02](../pruebas/casos/CP-02-caso-excepcion.md).

## Épica 5: Ventas y punto de venta

* `HU-02:` **Pedido desde la cotización aceptada.** Como trabajador (R-ATN), quiero confirmar el pedido desde la versión que aceptó el cliente, para que se genere la entrega por ubicación sin volver a digitarlo (RN-08, RN-09).
* `HU-03:` **Venta de mostrador.** Como trabajador (R-ATN), quiero registrar ventas rápidas en el punto de venta, para que el stock de la Tienda se descuente automáticamente en cada venta (RN-10).
* [ ] Configurar Ventas: plantillas de cotización y confirmación de pedidos.
* [ ] Configurar el punto de venta: métodos de pago (efectivo, tarjeta, Yape/Plin) y ubicación de la Tienda.

## Épica 6: Comprobantes, cobro y contabilidad

* `HU-04:` **Conciliación con KeyFacil.** Como propietario (R-FAC), quiero registrar en Odoo la referencia del comprobante emitido en KeyFacil y el cobro, para conciliar cada venta sin emitir dos veces (RN-11, RN-12).
* [ ] Instalar el módulo contable de la comunidad y definir qué registra frente a KeyFacil ([ADR-003](../arquitectura/decisiones/ADR-003-contabilidad.md), CA-07).
* [ ] Prueba de punta a punta: cotización aceptada → pedido → entrega → comprobante en KeyFacil → referencia y cobro en Odoo.

## Épica 7: Pendientes de decisión

Oportunidades identificadas que requieren decisión del equipo o de los propietarios antes de convertirse en historias.

* [ ] Unidades de medida y venta fraccionada (cable por metro, fierro por varilla, arena por m³).
* [ ] Proceso de crédito y cuentas por cobrar a clientes de obra (RN-15).
* [ ] Programación de reparto con la flota propia; base para el futuro SCM.
* [ ] Lista de precios con vigencia por producto para cemento y fierro (RN-03).
* [ ] Reporte diario de KeyFacil para la conciliación sin integración técnica (RN-11).
* [ ] Proceso de posventa y devoluciones de material sobrante (RN-13).
* [ ] Decisión sobre WMS (Odoo Inventario avanzado o sistema aparte) y reapertura de Compras para SCM (CA-04).
