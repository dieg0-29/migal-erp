# Flujo de gestión de inventario

## 1. Metadatos

* **Fecha:** 17/10/2026
* **Versión:** 0.1
* **Autores:** César Joaquín
* **Sistema:** ERP (Odoo 18 Community: Inventario)

## 2. Propósito

`[E][AS-IS]` Los ingresos y mermas se registran a mano, el stock no refleja las ventas de los distintos canales y no se sabe con certeza qué hay en cada punto físico. `[FN-01][FN-02]`

El flujo propuesto mantiene un registro único de movimientos por ubicación (Tienda, Almacén 1 y Almacén 2) que conecta las ventas de [O2C](../o2c/flujo.md) con las recepciones de [P2P](../p2p/flujo.md), sin ocultar diferencias físicas.

## 3. Inicio y fin

* **Inicio:** una recepción, una salida por venta, una transferencia entre ubicaciones o un conteo físico.
* **Fin:** movimiento validado con cantidades reales, o diferencia registrada y resuelta con autorización.

## 4. Actores

| Perfil | Participación |
|---|---|
| R-ALM | Registra recepciones, preparación, despachos, transferencias y conteos |
| R-PRO | Autoriza ajustes de inventario y decide ante faltantes |
| R-ATN | Origina salidas por venta de mostrador y consulta disponibilidad |

## 5. Entradas y salidas

| Entradas | Salidas |
|---|---|
| Pedido confirmado, venta de mostrador, recepción de proveedor, conteo físico | Movimientos por ubicación, stock disponible, diferencias registradas |

## 6. Flujo

| Paso | Movimiento | Actividad | Actor | Regla | Evidencia |
|---|---|---|---|---|---|
| 1 | Recepción | Contar la mercadería recibida y registrar la cantidad real en la ubicación de destino | R-ALM | RN-19 | Documento de entrada con cantidad real, daños y ubicación |
| 2 | Salida por pedido | Preparar y despachar desde la ubicación reservada; registrar lo entregado y lo pendiente | R-ALM | RN-09, RN-10 | Documento de salida vinculado al pedido |
| 3 | Salida por punto de venta | El stock de la Tienda se descuenta en el momento de cada venta | Sistema | RN-10 | Movimiento por venta `[S]` por validar en la instancia |
| 4 | Transferencia | Mover mercadería entre Tienda, Almacén 1 y Almacén 2 | R-ALM | RN-09 | Documento de transferencia con origen y destino |
| 5 | Conteo y ajuste | Contar, reportar la diferencia y regularizar solo con autorización de un propietario | R-ALM / R-PRO | RN-21, SOD-03 | Conteo, diferencia, motivo, autorización y movimiento de ajuste |

## 7. Excepciones

| Situación | Tratamiento | Regla |
|---|---|---|
| Stock registrado distinto del físico | No comprometer el faltante; reportar y ajustar con autorización | EXC-02, SOD-03 |
| Recepción parcial o dañada | Registrar lo real y mantener el saldo pendiente con el proveedor; no ajustar para ocultarlo | RN-20 |
| Faltante para un pedido | R-PRO decide entrega parcial, sustituto o reposición manual por P2P; no hay solicitud de compra automática | RN-09 |

## 8. Indicadores

Por definir. Los indicadores de recepción están en [P2P](../p2p/indicadores.md) (P2P-K-02).

## 9. Pendientes de validación

* Representación de Tienda, Almacén 1 y Almacén 2 como almacenes o ubicaciones en Odoo.
* Momento efectivo del descuento del punto de venta (ver [VER-02](../../arquitectura/versiones/VER-02-crm.md), CA-06).
* Valoración contable del inventario con el módulo de la comunidad ([ADR-003](../../arquitectura/decisiones/ADR-003-contabilidad.md)); no se da por hecho el asiento automático.

## 10. Historial de cambios

| Versión | Fecha | Autor | Cambio |
|---|---|---|---|
| 0.1 | 17/10/2026 | César Joaquín | Versión inicial; reemplaza el caso de uso de inventario y lo alinea con los perfiles, las tres ubicaciones y la exclusión de Compras |
