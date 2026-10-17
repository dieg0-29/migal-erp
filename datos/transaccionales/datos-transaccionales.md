# Datos transaccionales

## 1. Metadatos

* **Fecha:** 17/10/2026
* **Versión:** 0.1
* **Autores:** Brenda Mirano
* **Custodio:** R-PRO

## 2. Propósito

Describir los objetos que nacen y cambian durante cada operación, y cómo se enlazan. No hay extractos operativos reales en esta carpeta. Los eventos que crean cada objeto están en [INT-01](../../arquitectura/integraciones/INT-01-CRM-ERP.md).

## 3. Objetos

| Objeto | Origen / vínculo | Datos mínimos | Sistema |
|---|---|---|---|
| Consulta o interacción | Canal y contacto | Necesidad, fecha, responsable y referencia de comunicación | CRM |
| Oportunidad | Cuenta y contacto | Necesidad, madurez, competencia, acción y estado | CRM |
| Cotización y versión | Oportunidad | Fecha, líneas, precios, condiciones y versión | CRM |
| Decisión comercial | Cotización o necesidad | Motivo, decisor, momento y condición | CRM |
| Pedido | Versión aceptada | Cantidades, condiciones acordadas y soporte | ERP |
| Recepción, entrega o ajuste | Compra o pedido; ubicación | Cantidad real, documento, actor, fecha y diferencias | ERP |
| Comprobante | Referencia de KeyFacil y operación | Tipo, serie y número, importe y conciliación | KeyFacil / ERP |
| Pago | Obligación o comprobante | Soporte verificado, monto y saldo | ERP |
| Caso posventa | Operación de origen | Solicitud, decisión, ejecución y cierre | ERP |

Las definiciones de campos están en el [diccionario de datos](../diccionario/diccionario-datos.md).

## 4. Reglas de conservación

* Cada objeto conserva su identificador y el enlace al anterior; el número de factura no se usa como ID de toda la operación ([registro de identificadores](../trazabilidad/identificadores-y-linaje.md)).
* Una corrección relevante conserva valor anterior, posterior, motivo y actor.
* Los ejemplos usan datos `[SIM]`; no se suben conversaciones, comprobantes, cuentas ni datos crediticios reales ([tratamiento de datos](../privacidad/tratamiento-datos.md)).

## 5. Pendientes

* Política de retención; no se fijan plazos arbitrarios.
* Mecanismo real de versionado y seguimiento en Odoo, definición de importación y campos adicionales por evento.

## 6. Historial de cambios

| Versión | Fecha | Autor | Cambio |
|---|---|---|---|
| 0.1 | 17/10/2026 | Brenda Mirano | Versión inicial |
