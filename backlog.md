# Product Backlog: ERP Ferre & Inversiones MIGAL

## Épica 1: Diseño de Arquitectura y Procesos (Fase de Modelado)

Orientada a definir la estructura del sistema, los límites de integración y las reglas de negocio antes de la implementación técnica.

* [x] **Elaborar Documentos de Arquitectura (Modelo C4):** Diseñar y documentar los diagramas de Contexto (Nivel 1), Contenedores (Nivel 2) y Componentes (Nivel 3).
* [x] **Redactar Architecture Decision Records (ADRs):** Documentar la decisión técnica de la elección de ODOO como sistema ERP, así como la elección de su versión 18 y el "Odoo 18 Accounting Community" desarrollado por Odoo Mates.
* [x] **Modelar Procesos de Negocio TO-BE:** Redactar los flujos principales y alternativos para la Gestión de Inventarios y Gestión de Ventas

## Épica 2: Aprovisionamiento del Entorno Base

Preparación del servidor, la base de datos y la configuración inicial de la compañía en el ERP.

* [x] **Configurar Repositorio y Control de Versiones:** Inicializar el repositorio en GitHub, establecer reglas de protección de ramas y definir la estructura de carpetas (`/arquitectura`, `/procesos`, `/datos`).
* [ ] **Desplegar Entorno de Desarrollo:** Instalar la instancia inicial de Odoo 18 (Community) y configurar la base de datos PostgreSQL asociada al entorno.

## Épica 3: Implementación del Control de Inventario

Habilitar el control físico de la mercadería, estableciendo la topología de la empresa y la carga de datos maestros.

* `HU-01:` **Recepción y Ajustes sin Módulo de Compras:** Como operario de almacén, quiero registrar ingresos directos y ajustes manuales mediante documentos de recepción, para mantener el stock físico actualizado sin depender de un flujo de abastecimiento formal.
* [ ] **Configurar Topología de Almacenes:** Parametrizar en el módulo de Inventario la estructura física del negocio, conformada por una tienda principal y dos almacenes.
* [ ] **Carga Inicial del Catálogo de Productos:** Importar el archivo maestro de artículos con sus respectivas unidades de medida.

## Épica 4: Implementación de Canales Comerciales

Instalación y conexión de los módulos de venta orientados a distintos canales de atención, asegurando su comunicación con el inventario.

* `HU-02:` **Gestión de Pedidos Remotos (WhatsApp):** Como propietario, quiero transcribir los pedidos recibidos por WhatsApp en el módulo de Ventas, para que el sistema calcule los montos, reserve el stock automáticamente y genere las guías de salida.
* [ ] **Parametrizar Módulo de Ventas:** Instalar el módulo, configurar las plantillas de cotización y los flujos de confirmación de órdenes (`sale.order`).
* `HU-03:` **Ventas Rápidas en Tienda Física:** Como propietario en rol de cajero, quiero operar una interfaz ágil de Punto de Venta (POS) para transacciones de mostrador, de modo que el stock se descuente en un solo bloque al cerrar la venta.
* [ ] **Parametrizar Módulo Punto de Venta:** Instalar el módulo POS, configurar los métodos de pago (Efectivo, Tarjetas, Yape/Plin) y enlazar la caja a la ubicación de inventario de la Tienda Principal.

## Épica 5: Integración Financiera y Cierre (Contabilidad)

Incluye la automatización de los apuntes contables para garantizar la visibilidad del valor del inventario y los ingresos generados.

* `HU-04:` **Valoración Automática de Existencias:** Como propietario, quiero que cada movimiento validado en el almacén y cada cierre de caja genere automáticamente su asiento correspondiente, para evitar la digitación manual y la desconexión financiera.
* [ ] **Instalar Módulo Contable de Terceros:** Desplegar y habilitar el módulo "Odoo 18 Accounting Community" desarrollado por Odoo Mates.
* [ ] **Mapeo del Plan Contable:** Configurar las cuentas puente de inventario, las cuentas de ingresos por ventas y los diarios contables (Caja/Bancos, Ventas, Stock).
* [ ] **Pruebas de Integración (End-to-End):** Ejecutar un ciclo completo de prueba: registrar pedido remoto -> validar salida de almacén -> emitir factura interna -> verificar asiento contable generado.