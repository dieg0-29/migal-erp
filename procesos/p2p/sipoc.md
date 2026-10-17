# SIPOC — Procure to Pay

**Estado:** TO-BE propuesto; reglas RN-16 a RN-25 del [catálogo](../catalogo-reglas.md).

| Proveedores de información/recursos | Entradas | Proceso | Salidas | Clientes/receptores |
|---|---|---|---|---|
| Inventario, atención y propietarios | Faltante, conteo o compromiso comercial | Identificar y revisar necesidad | Solicitud priorizada y referencia | Propietarios |
| Proveedores y catálogo | Disponibilidad, precio, unidad, entrega y pago | Comparar y decidir compra | Condiciones y autorización | Proveedor / operación |
| Proveedor seleccionado | Mercadería y soporte | Recibir y comprobar cantidades | Recepción, diferencias y pendientes | Inventario / propietarios |
| Proveedor y registros internos | Documento, compra y recepción | Verificar obligación | Saldo validado o discrepancia | Función administrativa |
| Propietarios y medio de pago | Autorización y monto | Pagar, aplicar y conciliar | Pago verificable y cierre/excepción | Proveedor / propietarios |

## Inicio, fin y frontera

Inicio: necesidad identificada, no necesariamente un pedido de cliente. Fin: recepción y obligación conciliadas o excepción explícitamente cerrada. Inventario registra efecto físico; P2P explica autorización, condiciones y pago. La cotización comercial puede conservar una promesa condicionada, pero no ejecuta abastecimiento.

## Control de la información

Conservar referencias de producto/unidad, proveedor y compra en la recepción. Comparar documentos sin asumir que todos existen en un único sistema. En pagos anticipados conservar saldo económico y físico por separado. No se establecen plazos de crédito ni niveles mínimos de stock sin validar con propietarios.

## Validación pendiente

Confirmar procedimiento AS-IS, documentos disponibles, tratamiento de devoluciones y representación técnica. El modelo puede aplicarse manualmente antes de decidir el módulo Compras; no acredita automatización. Referencias: [flujo](flujo.md), [reglas](../catalogo-reglas.md), [fuentes del negocio](../../fuentes/fuentes-negocio.md).
