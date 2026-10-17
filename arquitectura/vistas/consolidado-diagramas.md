# Arquitectura del Sistema

Para plasmar la arquitectura del sistema ERP de Ferre & Inversiones MIGAL, se ha adoptado el Modelo C4 (Context, Containers, Components, Code)

## 1. Diagrama de Contexto (Nivel 1)

Ofrece la visión más general del sistema. Define los límites arquitectónicos del ERP Odoo 18 y cómo este interactúa con los usuarios clave y los sistemas externos.

![diagrama-contexto](c4/render/contexto.png)

---

## 2. Diagrama de Contenedores (Nivel 2)

Expone la infraestructura técnica subyacente. Se visualiza el cliente web, la base de datos centralizada en PostgreSQL, y los contenedores lógicos en Python correspondientes a los módulos seleccionados

![diagrama-contenedores](c4/render/contenedores.png)

---

## 3. Diagramas de Componentes (Nivel 3)

Profundiza en los contenedores específicos para revelar los componentes internos (modelos ORM y controladores lógicos) que ejecutan los flujos de negocio principales.

### 3.1. Order to Cash

Muestra la confirmación del pedido desde la cotización aceptada (frontera CRM a ERP, [INT-01](../integraciones/INT-01-CRM-ERP.md)), la entrega por ubicación, la venta de mostrador con descuento automático de stock y el registro de la referencia del comprobante emitido en KeyFacil. Odoo no emite comprobantes fiscales ([ADR-004](../decisiones/ADR-004-odoo-community-fronteras-crm-erp.md)). Flujo detallado: [O2C](../../procesos/o2c/flujo.md).

![componentes-ventas](c4/render/componentes/ventas.png)

### 3.2. Gestión de inventario

Muestra recepciones, entregas, transferencias y ajustes por ubicación (Tienda, Almacén 1 y Almacén 2). Los ajustes requieren autorización de un propietario (SOD-03) y la valoración contable automática queda por validar. Flujo detallado: [inventario](../../procesos/inventario/flujo.md).

![componentes-inventario](c4/render/componentes/inventario.png)

### 3.3. Escenario CRM previo al pedido

Muestra el recorrido comercial dentro del CRM de Odoo 18 Community: lead, calificación, actividades, cotización y motivos de pérdida. El método `action_confirm()` marca la frontera conceptual: hasta la cotización el CRM conserva el contexto comercial; desde la confirmación, el ERP compromete y ejecuta (ver ADR-004).

![componentes-crm](c4/render/componentes/crm.png)
