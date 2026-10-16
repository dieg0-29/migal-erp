# Flujo Principal: Gestion de Ventas

**Objetivo y Contexto:**
El objetivo de este flujo de trabajo es la gestion integral del ciclo de ventas de la ferreteria, haciendo uso de los modulos de "Punto de Venta", y "Ventas" que ofrece Odoo, estos a su vez estaran conectados al modulo de "Contabilidad" desarrollado por terceros para la version de Odoo Comunity.

El flujo actual (AS-IS) cuenta con problemas como
1. Falta de integracion de procesos (con Contabilidad)
2. Silos de informacion
3. Desconexion con inventarios

La intencion de este flujo es aprovecharlas funciones de Odoo Community para implementar un flujo "TO-BE" que permita la integración con contabilidad, la propagacion automatica de informacion (entre Ventas, Almacén y Compras), eliminar reprocesos manuales, asegurando que los procesos subsecuentes fluyan naturalmente desde la confirmación de la venta.

---

# Especificación del Caso de Uso: Flujo de Ventas

| 1.- Caso de Uso del Sistema | Gestión Integral de Ventas |
| :--- | :--- |
| **2.- Descripción del caso de uso** | Permite registrar y gestionar las ventas a través de dos canales: ventas rápidas de mostrador (Punto de Venta) y ventas mayoristas (Módulo Ventas). El flujo abarca desde la selección de productos y validación de stock, hasta la entrega de la mercancía y la generación automática de los apuntes contables en el módulo de contabilidad de terceros. |
| **3.- Actor(es)** | - **Cajero / Vendedor de Mostrador:** Gestiona ventas rápidas y cobros directos.<br>- **Ejecutivo de Ventas:** Gestiona presupuestos y pedidos mayoristas.<br>- **Operario de Almacén:** Despacha la mercancía de pedidos corporativos.<br>- **Sistema (Odoo + Contabilidad):** Ejecuta automatizaciones de stock e integracion de actividades. |
| **4.- Precondiciones** | - Los productos, precios e impuestos deben estar configurados en el sistema.<br>- El módulo de Contabilidad de terceros debe estar instalado y con los diarios contables (ventas, caja/bancos) mapeados correctamente.<br>- Las sesiones del Punto de Venta deben estar configuradas y abiertas por el cajero. |
| **5.- Postcondiciones** | - El inventario físico se reduce automáticamente en la cantidad despachada/vendida.<br>- Se generan automáticamente las facturas o boletas correspondientes.<br>- El sistema crea los apuntes contables (cuentas por cobrar, ingresos, caja) reflejando la transacción en la contabilidad general sin intervención manual. |

| 6.- Pasos (Flujo de Eventos: Módulo Ventas Mayoristas) | | |
| :--- | :--- | :--- |
| **Nro** | **Acción del Actor** | **Respuesta del Sistema** |
| 1 | El **Ejecutivo de Ventas** ingresa al módulo de Ventas, crea un "Presupuesto", asigna al cliente y agrega los productos. | El sistema calcula precios e impuestos, verificando en tiempo real la disponibilidad de inventario (alertando visualmente si no hay stock). |
| 2 | El **Ejecutivo de Ventas** hace clic en "Confirmar". | El sistema transiciona el Presupuesto a "Pedido de Venta" y genera automáticamente una "Guia de Salida" en el módulo de Inventario. |
| 3 | El **Operario de Almacén** revisa las órdenes de entrega, prepara la mercancía y hace clic en "Validar" la guia. | El sistema descuenta el stock físico del Kardex y marca el Pedido de Venta como listo para facturar. |
| 4 | El **Ejecutivo de Ventas** abre el Pedido de Venta y hace clic en "Crear Factura". | El sistema genera una factura borrador heredando toda la información del pedido y de la guia entregada. |
| 5 | El actor revisa la factura y hace clic en "Confirmar". | El sistema asigna un número correlativo legal a la factura y **genera automáticamente los registros contables** en el módulo de Contabilidad de terceros (Ingresos, Impuestos y Cuentas por Cobrar). |

| 6.1.- Flujo Alternativo 1: Ventas Rápidas (Punto de Venta / Mostrador) |
| :--- |
| **Paso 1:** El **Cajero** abre sesión en el "Punto de Venta" (POS).<br>**Paso 2:** El Cajero escanea o selecciona los productos en la interfaz. El sistema descuenta lógicamente el stock.<br>**Paso 3:** El Cajero selecciona el método de pago (Efectivo, Tarjeta) y valida la transacción.<br>**Respuesta del Sistema:** El sistema emite el ticket/comprobante, realiza la salida de inventario de forma instantánea y, al cerrar la sesión del POS, **consolida y publica automáticamente los registros contables** de todas las ventas del turno en el diario correspondiente. |

| 6.2.- Flujo Alternativo 2: Quiebre de Stock (MTO) en Ventas Corporativas |
| :--- |
| **Paso 2.1:** Al confirmar el Pedido de Venta, el sistema detecta falta de stock de un artículo configurado bajo pedido (Make To Order).<br>**Respuesta del Sistema:** Odoo genera la Guia de Salida en estado "Esperando" y, de forma paralela y automática, crea una Solicitud de Presupuesto en el módulo de Compras, rompiendo los silos de información y notificando la necesidad de abastecimiento sin requerimientos manuales. |

| 7.- Reglas de Negocio y Requerimientos Satisfechos |
| :--- |
| A continuación se detalla cómo el nuevo flujo "TO-BE" resuelve los problemas del escenario "AS-IS": |

| Problema / Requerimiento Original | Solución Implementada (Odoo TO-BE) |
| :--- | :--- |
| **Problema AS-IS 1:** Falta de integración de procesos (con Contabilidad) | Integración del módulo de Contabilidad de terceros. La confirmación de facturas en "Ventas" y el cierre de caja en "Punto de Venta" gatillan la creación inmediata de pólizas/asientos contables. |
| **Problema AS-IS 2:** Silos de información | Se establece una base de datos centralizada. Ventas, Inventario, Compras y Contabilidad leen del mismo maestro de clientes, productos y facturas. |
| **Problema AS-IS 3:** Desconexión con inventarios | Validación de stock en tiempo real al hacer la cotización. Descuento automático del Kardex al validar la guia o al cobrar en el POS. |
| **Regla de Negocio:** No vender sin stock (Salvo MTO) | El sistema bloquea o alerta las salidas en negativo. En su defecto, activa la ruta de abastecimiento automático (MTO) conectando Ventas con Compras de manera invisible para el vendedor. |

    MTO son las siglas de Make to Order (fabricación o reabastecimiento bajo pedido), hay casos donde la venta, sobre todo al por mayor y para obras, se realiza sin considerar el inventario ya que para estos casos se crea una orden de abastecimiento para satisfacer el pedido y se cordina el envio con el provedor.