# Alcance

**1. Objetivo General**
El proyecto comprende el diseño e implementación de una arquitectura ERP base en la nube, utilizando Odoo 18, para la empresa de venta al por menor Ferre & Inversiones MIGAL. El objetivo es centralizar y estructurar los procesos operativos de almacén, abastecimiento, ventas y contabilidad básica, transformando el modelo actual basado en cálculo mental y registros físicos informales en un flujo de datos integrado que brinde información precisa para la toma de decisiones.

**2. Límites del Sistema**
La primera liberación del ERP abarcará la configuración y puesta en marcha de los siguientes componentes:

* **Gestión de Almacén:** Implementación del control de inventario sincronizado y centralizado que cubra las ubicaciones físicas de la empresa, es decir, la tienda y los dos almacenes. Se automatizarán las alertas de reposición de stock hacia los proveedores, reemplazando el cálculo mental.
* **Gestión de Ventas Internas (Punto de Venta - POS):** Despliegue del módulo POS de Odoo para el registro formal de las ventas diarias que no requieran emisión de comprobantes fiscales.
* **Ingreso Manual de Pedidos Externos:** Las ventas cerradas a través de llamadas o mensajes de WhatsApp serán registradas manualmente por los propietarios en el ERP como órdenes de venta para asegurar la correcta rebaja del inventario.


**3. Exclusiones**
Para garantizar la viabilidad del producto mínimo, quedan excluidos de esta fase:

* **Facturación Electrónica Integrada:** No se implementará la localización peruana de Odoo para comprobantes de pago de la SUNAT. El sistema "KeyFacil" se mantendrá operando en paralelo y de forma aislada para la emisión exclusiva de facturas y boletas electrónicas.
* **Integración de API de WhatsApp:** No se automatizará la lectura, respuesta ni captura de pedidos por WhatsApp. Este seguirá operando únicamente como un canal de comunicación externo.