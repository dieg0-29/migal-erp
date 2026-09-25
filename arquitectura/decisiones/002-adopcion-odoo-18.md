# ADR 002: Adopcion de Odoo V18 Community

## 1. Metadatos
* **Fecha:** 25/09/2026
* **Estado:** Propuesto
* **Autores:** Gabriel Martinez A.

## 2. Contexto y Problema
Despues de la decision de tomar Odoo como el ERP a ser implementado nos encontramos con la necesidad de especificar la version de Odoo a usarse, para esto se tiene que considerar las funciones, integraciones y limitaciones de cada una de las versiones de Odoo comunity.

## 3. Restricciones de la Empresa (Drivers)
Ejemplos: presupuesto, falta de personal TI, necesidad de acceso multi-local, conectividad limitada, etc.
* Presupuesto: El presupuesto de la empresa es bajo, motivo por el cual se esta considerando el uso de la version comunity de Odoo.
* Falta de personal de TI: La falta de personal de TI dedicado significa que se necesita hacer uso de modulos y codigo ya desarrollado que requiera la menor cantidad de trabajo extra para funcionar.

## 4. Opciones Consideradas
| categoría | Odoo 18 | Odoo 19 | Odoo 20 |
|---|---|---|---|
| **compatibilidad de contabilidad externa** | Tiene alta disponibilidad de módulos OCA como account-financial-tools [1]. | Tiene módulos disponibles como om_account_accountant y account_usability [2]. | Los módulos de terceros requieren tiempo de migración comunitaria tras su lanzamiento [3]. |
| **localización fiscal** | Incluye paquetes base y soporte para Peppol PINT [4]. | Simplifica el mapeo de impuestos según secuencias de posición fiscal [5]. | Carece de integraciones locales inmediatas al depender de la migración externa [3]. |
| **rendimiento offline del punto de venta** | Las aplicaciones web progresivas (PWA) permiten la instalación en dispositivos móviles [4]. | Un perfil de permisos mínimos para personal reduce riesgos operativos [5]. | El sistema descubre hardware local mediante navegadores Chromium [6]. |
| **unidades de medida y fraccionamiento** | Usa funciones estándar de conversión. | Mantiene el soporte base de conversiones de medida. | Incorpora barras de progreso para promociones basadas en cantidades [6]. |
| **reglas de compras automáticas** | Valora el inventario con base en las facturas de los proveedores [4]. | Genera órdenes de compra automáticamente desde ventas mediante integración UBL [5]. | Predice retrasos y problemas de costos mediante inteligencia artificial [6]. |
| **valoración de inventario** | Calcula un margen de valoración simple sin usar la aplicación de inventario [4]. | Ejecuta la valoración en tiempo real sobre las facturas y usa los documentos más recientes [5]. | Usa agentes de inteligencia artificial para detectar anomalías contables [6]. |
| **dependencias de servidor** | Mantiene la arquitectura base de PostgreSQL y Python. | Agrega capacidades de automatización que requieren recursos estándar [5]. | Soporta más de 10 000 usuarios concurrentes mediante bases de datos de réplica de lectura [6]. |
| **control de arqueos de caja** | Genera recibos compatibles con el estándar JoFotara [4]. | Ofrece un modo oscuro nativo y validación de pago con un clic en el POS [5]. | Adapta la personalización del panel de control según los roles de usuario [6]. |
| **protocolos de integración** | Autentica a los usuarios mediante passkeys con el protocolo webauthn [4]. | Modifica la gestión de usuarios y grupos para un control más seguro [5]. | Incluye un servidor Model Context Protocol (MCP) nativo para consultas de inteligencia artificial [6]. |

## 5. Decisión
Hemos tomado la decision de usar Odoo V18 Comunity

## 6. Justificación
Se ha tomado esta decision debido a la mayor disponibilidad de modulos, integraciones, guias y facilidad de implementacion. Odoo V20 es el primero en ser descartado, al ser reciente no existe amplia documentacion y experiencia que pueda usarse de guia y las funcionalidades extra que ofrece no son suficiente para justificar su eleccion, entre Odoo V18 y V19 la decision se da debido a la mayor documentacion disponible para la version V18 y la mayor simplicidad de sus funciones, que reduciran la dificultad de adaptar las mismas al negocio.

## 7. Consecuencias (Trade-offs)
* **Positivas:** Mas facil integracion, simplicidad para adaptar al negocio, extensiva documentacion.
* **Negativas / Riesgos:** Ausencia de "features" actuales (IA), menor capacidad para crecimiento en comparacion con V19 y V20. 

## Fuentes

[1] Odoo Community Association (OCA). Repositorio de herramientas financieras: https://github.com/OCA/account-financial-tools \
[2] Odoo Mates. Odoo 19 Community: FREE Accounting with OCA: https://www.youtube.com/watch?v=ZpgAVDO5P2s \
[3] Odoo. Ciclo de vida de versiones soportadas: https://www.odoo.com/page/editions \
[4] Odoo. Notas de la versión 18: https://www.odoo.com/odoo-18-release-notes \
[5] Odoo. Notas de la versión 19: https://www.odoo.com/odoo-19-release-notes \
[6] Odoo. Notas de la versión 20: https://www.odoo.com/odoo-20-release-notes 
