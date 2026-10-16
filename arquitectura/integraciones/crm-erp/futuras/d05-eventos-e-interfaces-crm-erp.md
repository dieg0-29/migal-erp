# D05: Evaluación de Eventos y Fronteras de Información CRM–ERP

## 1. Metadatos


* **Fecha:** 16/10/2026
* **Estado:** Evaluación conceptual hacia el Examen Parcial
* **Autores:** Gabriel Gibson Martínez Arista

## 2. Propósito y Alcance

Este documento identifica los momentos en que la información cambia de responsabilidad entre Atención, CRM, Ventas, Inventario, Administración y KeyFacil.

El término “evento” se utiliza aquí como un hito de negocio. No implica que exista un evento técnico publicado mediante una API o un sistema de mensajería.

## 3. Alcance

### Incluido en el corte actual

* consulta inicial;
* registro del contacto;
* calificación de la oportunidad;
* elaboración de cotización.

### Proyectado

* confirmación del pedido;
* preparación y entrega;
* facturación;
* cobro;
* posventa.

## 4. Hitos de Información

| Hito | Actor que inicia | Información utilizada | Receptor funcional | Estado |
|---|---|---|---|---|
| Consulta recibida | Cliente o maestro de obra | Datos de contacto y necesidad inicial. | CRM / Ventas | Actual |
| Oportunidad calificada | Ventas | Materiales, cantidades y relación con obra. | CRM / Ventas | Actual |
| Cotización elaborada | Ventas | Productos, unidades, cantidades y precios. | Cliente | Actual |
| Pedido confirmado | Cliente / Ventas | Cotización aceptada y condición comercial. | Ventas / Inventario | Futuro |
| Entrega preparada | Almacén | Existencia, ubicación y cantidades. | Cliente / Administración | Futuro |
| Comprobante emitido | Administración | Tipo, número e importe del comprobante. | Pedido / Cliente | Futuro |
| Pago registrado | Administración | Monto, forma de pago y saldo. | Administración / Propietarios | Futuro |
| Posventa registrada | Cliente / Ventas | Reclamo, cambio, devolución o resolución. | Ventas / Inventario | Futuro |

## 5. Fronteras Funcionales

### Frontera 1: Canales hacia CRM

Los canales de atención proporcionan información inicial. El sistema debe registrar únicamente los datos necesarios para identificar y dar seguimiento a la consulta.

### Frontera 2: CRM hacia Ventas

La oportunidad puede convertirse en una cotización utilizando el contacto existente y los productos del catálogo.

Debe validarse en Odoo si la conversión conserva todos los datos esperados.

### Frontera 3: Ventas hacia Inventario

La confirmación de una venta puede generar o activar una operación de entrega, según la configuración utilizada.

Debe comprobarse:

* cómo se consulta la disponibilidad;
* cuándo se reserva inventario;
* cómo se registra una entrega parcial;
* cómo se maneja un faltante.

### Frontera 4: Ventas e Inventario hacia Administración

Administración requiere conocer qué se vendió y qué se entregó para emitir o registrar el comprobante correspondiente.

### Frontera 5: Administración hacia KeyFacil

En el alcance actual no se define una interfaz técnica. KeyFacil se considera un sistema externo cuya referencia debe registrarse y conciliarse manualmente hasta que exista una decisión distinta.

## 6. Datos Mínimos por Hito

| Hito | Datos mínimos propuestos |
|---|---|
| Consulta | Nombre o referencia, teléfono y canal. |
| Oportunidad | Necesidad, productos aproximados y cantidades estimadas. |
| Cotización | Cliente, productos, unidades, cantidades y precios. |
| Pedido | Cotización aceptada, condición comercial y datos necesarios para continuar. |
| Entrega | Punto físico, cantidad entregada y cantidad pendiente. |
| Comprobante | Referencia de KeyFacil, importe y tipo de comprobante. |
| Cobro | Monto pagado, forma de pago y saldo. |

## 7. Pendientes de Validación

* Validar la conversión de CRM a Ventas.
* Validar las reservas de inventario.
* Validar las entregas parciales.
* Definir el modelo de almacenes y ubicaciones.
* Definir el momento exacto de facturación.
* Definir la referencia mínima de KeyFacil.
* Determinar si en una fase posterior será necesaria una interfaz técnica.