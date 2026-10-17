# Flujo Order to Cash: del pedido al cobro

## 1. Metadatos

* **Fecha:** 17/10/2026
* **Versión:** 0.1
* **Autores:** César Joaquín
* **Sistema:** ERP (Odoo 18 Community: Ventas, Punto de Venta, Inventario y contabilidad básica) y KeyFacil (externo)

## 2. Propósito

`[E][AS-IS]` Las ventas se registran en notas y en la memoria de los propietarios, el stock no se descuenta al vender y la facturación en KeyFacil no queda vinculada a la operación. `[FN-01][FN-02]`

El flujo propuesto ejecuta en el ERP lo que se acordó con el cliente: confirma el pedido, prepara y entrega la mercadería desde la ubicación correcta, registra la referencia del comprobante emitido en KeyFacil y el cobro, y cierra la operación sin pendientes ocultos.

## 3. Inicio y fin

* **Inicio:** cotización aceptada en el CRM ([INT-01](../../arquitectura/integraciones/INT-01-CRM-ERP.md), F-02), o venta de mostrador en el punto de venta.
* **Fin:** entrega y cobro conciliados, o excepción cerrada con motivo.

La etapa comercial previa (consulta, oportunidad y cotización) está en el [flujo comercial](../comercial-crm/flujo-comercial.md).

## 4. Actores

| Perfil | Participación |
|---|---|
| R-ATN | Confirma el pedido desde la cotización aceptada; atiende ventas de mostrador |
| R-PRO | Decide crédito, cambios posteriores a la aceptación y faltantes; emite el comprobante en KeyFacil |
| R-ALM | Prepara, despacha y registra cantidades realmente entregadas |
| R-FAC | Registra la referencia del comprobante, el cobro y la conciliación (lo ejercen los propietarios) |

## 5. Entradas y salidas

| Entradas | Salidas |
|---|---|
| Cotización aceptada (versión y condiciones) o venta de mostrador; stock por ubicación; datos fiscales si el comprobante los requiere | Pedido, entrega con cantidades reales, referencia del comprobante de KeyFacil, cobro aplicado, cierre |

## 6. Flujo

### 6.1. Venta con pedido (obra o mayorista)

| Paso | Actividad | Actor | Sistema | Regla | Evidencia |
|---|---|---|---|---|---|
| 1 | Confirmar el pedido desde la versión aceptada, con la identificación que exija el comprobante | R-ATN | ERP (Ventas) | RN-07, RN-08 | Pedido vinculado a la versión aceptada |
| 2 | Si hay condición de crédito nueva o modificada, decidirla | R-PRO | ERP | RN-15, SOD-04 | Condición, fundamento y responsable |
| 3 | Consultar disponibilidad y reservar en la ubicación de salida (Tienda, Almacén 1 o Almacén 2) | R-ALM | ERP (Inventario) | RN-09 | Cantidad solicitada, disponible y reservada por ubicación |
| 4 | Preparar y despachar; registrar la cantidad realmente entregada | R-ALM | ERP (Inventario) | RN-10 | Documento de salida, cantidad entregada y pendiente |
| 5 | Emitir el comprobante en KeyFacil | R-PRO | KeyFacil | RN-11 | Comprobante emitido fuera de Odoo |
| 6 | Registrar la referencia del comprobante y conciliar con el pedido | R-FAC | ERP | RN-11 | Referencia, importe y conciliación |
| 7 | Registrar el cobro verificado y el saldo | R-FAC | ERP | RN-12 | Soporte, monto y saldo |
| 8 | Cerrar con entrega, cobro e incidencias resueltos | R-PRO | ERP | RN-14 | Estado de cierre y responsable |

Detalle de los pasos 1 y 2: [pedido](pedido.md). Detalle de los pasos 5 y 6: [facturación](facturacion.md).

### 6.2. Venta de mostrador (punto de venta)

| Paso | Actividad | Actor | Sistema | Regla | Evidencia |
|---|---|---|---|---|---|
| 1 | Registrar los productos y el cobro en el punto de venta | R-ATN | ERP (Punto de Venta) | RN-12 | Ticket interno y pago |
| 2 | El sistema descuenta automáticamente el stock de la Tienda en el momento de la venta, sin intervención de almacén | Sistema | ERP (Inventario) | RN-10 | Movimiento de salida por venta `[S]` por validar en la instancia |
| 3 | Emitir el comprobante en KeyFacil y registrar su referencia | R-PRO / R-FAC | KeyFacil / ERP | RN-11 | Referencia conciliada con la venta |
| 4 | Al cerrar la sesión, conciliar el efectivo y los pagos con las ventas del turno | R-FAC | ERP (Punto de Venta) | RN-12 | Cierre de sesión con diferencias explicadas |

El ticket del punto de venta es un registro interno; el comprobante fiscal lo emite KeyFacil ([ADR-004](../../arquitectura/decisiones/ADR-004-odoo-community-fronteras-crm-erp.md)).

## 7. Excepciones

| Situación | Tratamiento | Regla |
|---|---|---|
| Stock insuficiente al confirmar | R-PRO decide entre entrega parcial, sustituto o reposición manual por P2P; no se genera una compra automática | RN-09, RN-16 |
| Entrega parcial | Se registra lo entregado y el saldo pendiente queda visible | RN-10 |
| Cambio posterior a la aceptación | Decide R-PRO; nueva versión y aceptación si cambia lo acordado | SOD-05 |
| Diferencia entre comprobante y pedido | Se mantiene en revisión; no se corrige la cotización para que coincida | RN-11 |
| Pago duplicado o sin soporte | No se aplica hasta verificarlo | RN-12 |
| Cancelación | Se revisan movimientos, comprobantes y pagos antes de cerrar; no se borra el historial | RN-14 |

## 8. Indicadores

[Indicadores O2C](indicadores.md): O2C-K-05 a O2C-K-07 para entrega, conciliación fiscal y cobro.

## 9. Pendientes de validación

* Momento real del descuento de stock del punto de venta y de los asientos contables en la instancia (ver [VER-02](../../arquitectura/versiones/VER-02-crm.md), CA-06 y CA-07).
* Generación del documento de entrega al confirmar el pedido, reservas y entregas parciales.
* Alcance del módulo contable de la comunidad ([ADR-003](../../arquitectura/decisiones/ADR-003-contabilidad.md)): qué registra el ERP y qué queda solo en KeyFacil.

## 10. Historial de cambios

| Versión | Fecha | Autor | Cambio |
|---|---|---|---|
| 0.1 | 17/10/2026 | César Joaquín | Versión inicial; reemplaza el caso de uso de ventas y lo alinea con KeyFacil como emisor, la exclusión de Compras y los perfiles del modelo de autorización |
