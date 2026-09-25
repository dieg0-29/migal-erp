# ERP Ferre & Inversiones MIGAL - Grupo 1

Este repositorio contiene la documentación arquitectónica para la implementación de un sistema ERP basado en Odoo 18 para la empresa ferretera Ferre & Inversiones MIGAL. El propósito del proyecto es centralizar la gestión de inventarios y ventas, eliminando la dependencia de registros informales y cálculos mentales, para lograr la trazabilidad de las operaciones diarias y facilitar la toma de decisiones basada en datos precisos.

## Problema de Integración

Actualmente, Ferre & Inversiones MIGAL sufre de una desconexión operativa y falta de trazabilidad. Los procesos dependen de la memoria de los dueños (precios variables, registro de compras mental) y de canales no centralizados (pedidos por WhatsApp sin horario fijo). Aunque utilizan Keyfacil para algunas facturaciones electrónicas, el registro de ventas físicas en papel,  el manejo de créditos y cobranzas manual (cuadernos) genera un desorden en el almacén físico, dificulta la gestión de entregas y crea un vacío de información sobre las ganancias reales y la valoración del inventario.

## Alcance

**1. Objetivo General**
El proyecto comprende el diseño de una arquitectura ERP, utilizando Odoo 18, para la empresa de venta al por menor Ferre & Inversiones MIGAL. El objetivo es centralizar y estructurar los procesos operativos de almacén, abastecimiento, ventas y contabilidad básica, transformando el modelo actual basado en cálculo mental y registros físicos informales en un flujo de datos integrado que brinde información precisa para la toma de decisiones.

**2. Límites del Sistema**

* **Gestión de Almacén:** Control de inventario sincronizado y centralizado que cubra las ubicaciones físicas de la empresa, es decir, la tienda y los dos almacenes. Se automatizarán las alertas de reposición de stock hacia los proveedores, reemplazando el cálculo mental.
* **Gestión de Ventas Internas (Punto de Venta - POS):** Módulo POS de Odoo para el registro formal de las ventas diarias que no requieran emisión de comprobantes fiscales.
* **Ingreso Manual de Pedidos Externos:** Las ventas cerradas a través de llamadas o mensajes de WhatsApp serán registradas manualmente por los propietarios en el ERP como órdenes de venta para asegurar la correcta rebaja del inventario.

**3. Exclusiones**

* **Facturación Electrónica Integrada:** No se implementará la localización peruana de Odoo para comprobantes de pago de la SUNAT. El sistema "KeyFacil" se mantendrá operando en paralelo y de forma aislada para la emisión exclusiva de facturas y boletas electrónicas.
* **Integración de API de WhatsApp:** No se automatizará la lectura, respuesta ni captura de pedidos por WhatsApp. Este seguirá operando únicamente como un canal de comunicación externo.

## Integrantes

Equipo de trabajo conformado para el curso GE703 - Sistemas Integrados Empresariales:

* **Alejandro Cesar Flores Marcos** - Facilitador

* **Brenda Nicole Mirano Flores** - Producto

* **César Emmerson Joaquin Palomino** - Procesos

* **Diego Alonso Pinedo Aponte** - Arquitectura

* **Gabriel Gibson Martinez Arista** - Datos

* **Luis Rodrigo Nuñez Principe** - Validación
