# Pedido de cliente

**Estado:** diseño funcional; no acredita configuración de Ventas ni prueba de confirmación. Forma parte del [flujo O2C](flujo.md), pasos 1 y 2.

## Propósito y frontera

Convertir una propuesta aceptada en un compromiso operativo reconstruible. Una cotización enviada, una probabilidad alta o una conversación sin aceptación clara no son un pedido confirmado.

## Entradas y responsables

Cuenta/contacto, cotización y versión, productos/unidades/cantidades, precios y condiciones aceptadas, soporte de aceptación y datos de entrega si aplica. R-ATN prepara la transición; R-PRO resuelve excepciones; R-ALM recibe solo el compromiso confirmado y la información necesaria para ejecutar. No exigir datos adicionales que no correspondan a la operación.

## Flujo propuesto

| Paso | Acción | Evidencia / condición |
|---|---|---|
| 1 | Identificar qué versión acepta el cliente y quién comunica | Versión y soporte; validar representación del contacto si procede |
| 2 | Revisar precios, condiciones y excepciones pendientes | Decisión documentada; no confirmar sobre una oferta sustituida sin acuerdo |
| 3 | Comprobar información operativa disponible | Cantidad, destino y promesa; incertidumbre explícita |
| 4 | Registrar confirmación cuando se satisfagan condiciones | Referencia del pedido, momento y responsable |
| 5 | Relacionar preparación/entrega futura | Cantidades por estado, ubicación y documentos |
| 6 | Gestionar cambios posteriores | Motivo, anterior/posterior y nueva aceptación si cambia lo acordado |

## Excepciones

Faltante: consultar alternativa, parcial o reposición con decisión explícita, sin presumir RFQ automática. Crédito/descuento pendiente: mantener revisión. Cambio de cliente, cantidades o dirección: revisar impacto y conservar evidencia. Cancelación: comprobar movimientos, comprobantes y pagos existentes antes de cerrar; no borrar historia.

## Aceptación y pendientes

La prueba futura debe demostrar vínculo con versión aceptada, conservación de condiciones y efecto real de confirmar en el entorno. Verificar reservas, parciales, permisos y mapeo de campos; no afirmar bloqueos nativos ni crear un objeto separado si la instancia conserva la transición en el mismo registro.

Referencias: [INT-01](../../arquitectura/integraciones/INT-01-CRM-ERP.md), [catálogo de reglas](../catalogo-reglas.md) (RN-07, RN-08, RN-15), [ADR-004](../../arquitectura/decisiones/ADR-004-odoo-community-fronteras-crm-erp.md), [INT-01](../../arquitectura/integraciones/INT-01-CRM-ERP.md), [fuentes](../../fuentes/fuentes-negocio.md).
