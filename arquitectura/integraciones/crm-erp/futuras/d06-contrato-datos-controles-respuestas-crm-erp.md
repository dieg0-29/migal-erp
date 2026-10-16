# D06: Datos y Validaciones para la Transición CRM–ERP

## 1. Metadatos

* **Fecha:** 16/10/2026
* **Estado:** Diseño conceptual futuro hacia el Examen Parcial
* **Autores:** Gabriel Gibson Martínez Arista

## 2. Propósito y Alcance

Este documento identifica los datos que deben completarse progresivamente cuando una oportunidad comercial se convierte en cotización y posteriormente en pedido.

No constituye un contrato técnico de mensajes ni una especificación de API. Las validaciones descritas son propuestas funcionales pendientes de comprobación.

## 3. Grupos de Información

| Grupo | Datos incluidos | Momento de uso |
|---|---|---|
| Contacto y relación comercial | Identificador, nombre, teléfono, canal y maestro de obra opcional. | Consulta y calificación. |
| Identificación fiscal | Tipo y número de documento, según corresponda. | Confirmación y facturación. |
| Materiales y precios | Producto, unidad, cantidad, precio y descuento. | Cotización. |
| Disponibilidad y entrega | Punto físico, cantidad disponible, cantidad entregada y pendiente. | Confirmación y despacho. |
| Comprobante y pago | Referencia, importe, estado de facturación y estado de cobro. | Facturación y cierre. |

## 4. Validaciones Propuestas

### 4.1. Contactos

* Buscar contactos existentes antes de crear uno nuevo.
* Utilizar teléfono, nombre o documento como criterios de búsqueda.
* Evitar crear una ficha nueva para cada canal de atención.
* Registrar la relación con el maestro de obra como dato opcional.

### 4.2. Productos y precios

* Utilizar productos del catálogo activo.
* Mantener una unidad de medida clara.
* Evitar escribir productos libres cuando exista un producto catalogado.
* Revisar los precios antes de enviar la cotización.
* Registrar los descuentos especiales como condiciones sujetas a autorización.

### 4.3. Stock y entrega

* Consultar la disponibilidad registrada.
* Identificar el punto físico de salida.
* Comparar cantidad solicitada con cantidad disponible.
* Registrar la cantidad realmente entregada.
* Mantener visible cualquier cantidad pendiente.

### 4.4. Facturación y cobro

* Registrar la referencia del comprobante emitido en KeyFacil.
* Separar estado de facturación y estado de cobro.
* Registrar el monto pagado y el saldo pendiente.
* Validar los requisitos fiscales conforme al procedimiento aprobado por MIGAL.

## 5. Situaciones de Transición

### Situación 1: Paso directo

El cliente acepta la cotización, las condiciones están aprobadas y existe disponibilidad suficiente.

**Acción propuesta:**

* confirmar el pedido;
* preparar la entrega;
* registrar la facturación y el cobro según corresponda.

### Situación 2: Entrega parcial o distribuida

Los materiales están repartidos entre varios puntos físicos o no existe suficiente cantidad en un solo punto.

**Acción propuesta:**

* informar al cliente;
* registrar lo entregado;
* mantener el saldo pendiente;
* acordar la continuación de la entrega.

### Situación 3: Condición pendiente de autorización

El cliente solicita descuento especial o crédito no autorizado.

**Acción propuesta:**

* mantener la operación en revisión;
* solicitar autorización;
* no asumir que el sistema bloqueará automáticamente el pedido;
* registrar la decisión tomada.

### Situación 4: Datos incorrectos o cotización desactualizada

Los precios cambiaron, el documento requiere corrección o no existe disponibilidad.

**Acción propuesta:**

* actualizar la cotización;
* corregir los datos;
* registrar el motivo;
* evitar generar una entrega o comprobante hasta resolver la condición.

## 6. Contraste con Odoo

No debe afirmarse que Odoo bloqueará automáticamente descuentos, créditos, precios o faltantes sin realizar una prueba en la instancia concreta.

La evaluación debe distinguir entre:

* funcionalidad estándar;
* configuración de permisos;
* reglas del inventario;
* procedimiento manual;
* personalización futura.

Los resultados deben documentarse en B03.

## 7. Pendientes

* Definir datos mínimos obligatorios para confirmar un pedido.
* Validar los requisitos de facturación.
* Confirmar el modelo de inventario.
* Probar entregas parciales.
* Definir responsables de autorización.
* Definir cómo se registrarán los comprobantes de KeyFacil.
* Determinar qué controles requieren configuración o desarrollo futuro.