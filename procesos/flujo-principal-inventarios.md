## flujo principal: Gestión de Inventarios

**Objetivo y Contexto:**
El objetivo de este flujo de trabajo es la gestión centralizada de los movimientos de mercadería mediante el módulo de inventario de Odoo. Tiene por objetivo el integrar la inforamcion de inventario con los demas procesos y centralizar la misma, recibe instrucciones de salida de los módulos de ventas y punto de venta (pos), sincroniza las variaciones de valor del stock con el módulo de contabilidad, los ingresos de mercadería se gestionan de forma directa porque no se implementa el módulo de compras en esta etapa.

El flujo actual presenta los siguientes problemas:
1. Desconexión entre los movimientos físicos y su impacto contable.
2. Falta de trazabilidad del stock en tiempo real al vender por distintos canales.
3. Registro manual de ingresos y mermas con errores de digitación.

Este flujo usa las funciones de Odoo Community para implementar un estado propuesto. Las salidas se mecanizan a través de las ventas. Los ingresos se registran de manera directa. Toda variación física genera automáticamente su respectivo apunte de valoración en la contabilidad general.

---

## Especificación del Caso de Uso: Flujo de Gestión de Inventarios

| 1.- Caso de Uso del Sistema | Gestión de movimientos y ajustes de inventario |
| :--- | :--- |
| **2.- Descripción del caso de uso** | Registra ingresos directos de mercadería, procesa despachos originados por ventas comerciales y de mostrador, y realiza ajustes por mermas o inventario físico. El sistema centraliza el kardex y automatiza la valoración contable del stock sin depender del módulo de compras. |
| **3.- Actor(es)**| - Operario de almacén: prepara pedidos y realiza recepciones manuales.<br>- Jefe de almacén: autoriza ajustes de inventario y supervisa el kardex.<br>- Sistema (odoo + contabilidad): ejecuta la reducción o incremento de stock, sincronización multicanal y registros contables. |
| **4.- Precondiciones** | - Los artículos tienen configuración de productos almacenables.<br>- Las ubicaciones y almacenes lógicos tienen configuración en el sistema.<br>- El módulo de contabilidad de terceros tiene enlace con las cuentas de valoración de inventario y variación de existencias. |
| **5.- Postcondiciones** | - El stock físico y el stock previsto se actualizan en tiempo real.<br>- El sistema genera un registro inmutable en el historial de movimientos (kardex).<br>- El sistema emite automáticamente el asiento contable con el incremento o disminución del valor del inventario. |

| 6.- Pasos (Flujo de Eventos: Ingreso manual y ajuste de inventario) | | |
| :--- | :--- | :--- |
| **Nro** | **Acción del Actor** | **Respuesta del Sistema** |
| 1 | El operario de almacén ingresa al módulo de inventario y crea una recepción manual o un ajuste de inventario. | El sistema despliega el formulario solicitando la ubicación de destino y habilitando la selección de productos del catálogo. |
| 2 | El operario de almacén agrega los productos recibidos y digita las cantidades físicas reales ingresadas. | El sistema verifica el tipo de producto almacenable y muestra el stock actual a modo de comparativa. |
| 3 | El jefe de almacén revisa el documento y selecciona validar. | El sistema suma las unidades al stock físico disponible de manera inmediata e impide modificaciones posteriores a este documento. |
| 4 | El jefe de almacén consulta el reporte de movimientos de productos. | El sistema muestra la trazabilidad del ingreso con fecha, hora, documento de origen y usuario responsable. |
| 5 | Automatización del sistema. | El sistema genera automáticamente los registros contables en el módulo de contabilidad con débito a la cuenta de inventario y crédito a la cuenta puente de entradas, reflejando el nuevo valor del almacén. |

| 6.1.- Flujo Alternativo 1: salidas por ventas mayoristas (módulo ventas) |
| :--- |
| **Paso 1:** El sistema genera automáticamente una guia de salida en el panel de inventario al confirmarse un pedido de venta en el módulo comercial.<br>**Paso 2:** El operario de almacén abre el documento, verifica la disponibilidad reservada por el sistema y prepara la mercadería.<br>**Paso 3:** El operario selecciona validar.<br>**Respuesta del sistema:** El sistema descuenta el stock físico, cambia el estado del pedido a entregado para habilitar su facturación, y genera el asiento contable de costo de ventas y disminución de inventario. |

| 6.2.- Flujo Alternativo 2: descuento automático por punto de venta (pos) |
| :--- |
| **Paso 1:** El cajero realiza múltiples transacciones de venta rápida durante su turno.<br>**Paso 2:** El cajero realiza el cierre de sesión en el pos al finalizar la jornada.<br>**Respuesta del sistema:** Odoo agrupa todas las salidas de mostrador y ejecuta una guia de salida consolidada. Descuenta el stock físico del almacén asociado a la tienda y contabiliza la disminución del inventario sin requerir validación manual del personal de almacén. |

| 7.- Reglas de Negocio y Requerimientos Satisfechos |
| :--- |
| A continuación se detalla cómo el nuevo flujo "TO-BE" resuelve los problemas del escenario "AS-IS": |

| Problema / Requerimiento Original | Solución Implementada (Odoo TO-BE) |
| :--- | :--- |
| **Problema AS-IS 1:** : Desconexión entre los movimientos físicos y contabilidad | Automatización de la valoración de inventarios. Toda validación de entrada o salida genera de manera instantánea su apunte en el módulo de contabilidad de terceros. |
| **Problema AS-IS 2:** : Falta de trazabilidad en tiempo real del stock multicanal | Existencia de un kardex único y centralizado. Las ventas de pos reducen el stock al cerrar caja. Los pedidos de venta reservan mercadería en el acto para evitar sobreventas. |
| **Problema AS-IS 3:** : Registro manual de salidas con errores | Eliminación de la doble digitación. Las guias de salida heredan los productos y cantidades del documento de venta original. |
| **Regla de Negocio:** Independencia operativa del abastecimiento | El inventario soporta ingresos a través de recepciones directas y plantillas de ajustes por la ausencia del módulo de compras. Mantiene la rigurosidad del control físico y contable. |