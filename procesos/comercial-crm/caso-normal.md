# Caso normal — Cotización de materiales para obra

**Tipo:** recorrido documental sintético; no ejecutado en Odoo.  
**Corte:** PC2, antes del pedido confirmado.  
**Objetivo:** recuperar contexto del cliente, preparar una propuesta y registrar seguimiento sin excepción de precio.

## Datos reutilizados

| Objeto | Identificador / valor del catálogo |
|---|---|
| Cuenta | CLI-SIM-001 · Cliente Obra Alfa |
| Contacto | CON-SIM-002 · Maestro Alfa |
| Dirección de contexto | DIR-SIM-001 · Obra Alfa |
| Oportunidad | OPP-SIM-001 · Lista completa para obra |
| Fuente | Referido maestro |
| Canal de esta interacción | WhatsApp, supuesto del recorrido SIM; no deducido de la fuente |
| Cotización | COT-SIM-001-V01 |
| Seguimiento | Confirmar aprobación del responsable; 17/10/2026; Propietaria |

Todos los nombres, ubicaciones e importes son simulados. El dato de canal propuesto complementa el recorrido; el catálogo mezcla algunos conceptos en `origen` y debe mantener fuente y canal diferenciados al implementarse.

## Precondiciones

- Cuenta, contacto y dirección se pueden localizar en el catálogo sintético.
- La persona que atiende dispone de la lista y revisa la relación entre interlocutor y responsable económico.
- La propietaria revisa precios para el ejemplo. No se presupone permiso técnico configurado.

## Recorrido esperado

| Paso | Acción | Evidencia propuesta |
|---|---|---|
| 1 | Maestro Alfa comunica lista; se busca la cuenta existente | Interacción referida a CLI-SIM-001 y CON-SIM-002 |
| 2 | Se contextualiza la necesidad en Obra Alfa | Vínculo con DIR-SIM-001; no usar como orden de entrega |
| 3 | Se mantiene OPP-SIM-001 con probabilidad Alta y responsable | Necesidad concreta y lista; probabilidad cualitativa, no garantía de compra |
| 4 | Se prepara COT-SIM-001-V01 con precios de referencia sin ajuste | Líneas y versión identificables |
| 5 | Se registra disponibilidad/promesa pendiente de comprobación si el cliente solicita fecha | Condición y responsable; ningún movimiento de stock |
| 6 | Se conserva comprobante previsto “Por definir” | Dato fiscal no exigido universalmente para cotizar |
| 7 | Se propone comunicar la cotización al contacto y confirmar revisión del responsable | Registro de envío a obtener; no afirmar envío realizado |
| 8 | Se fija próxima acción el 17/10/2026 a cargo de Propietaria | Acción y responsable del catálogo |

## Líneas y comprobación aritmética

| Producto | Cantidad | Precio SIM | Importe SIM |
|---|---:|---:|---:|
| PRD-SIM-001 · Cemento | 100 bolsas | S/ 30.00 | S/ 3,000.00 |
| PRD-SIM-002 · Fierro | 40 unidades | S/ 40.00 | S/ 1,600.00 |
| PRD-SIM-003 · Tubería PVC | 20 unidades | S/ 20.00 | S/ 400.00 |
| **Suma de líneas** | | | **S/ 5,000.00** |

La suma es cantidad × precio ofrecido y no añade impuestos, flete ni descuentos no especificados. No se presenta como total fiscal. El Excel mantiene la cotización “En revisión” y la oportunidad “Abierta”; comunicarla es un paso esperado del recorrido y requiere evidencia para cambiar su estado.

## Resultado esperado y validación pendiente

Se puede reconstruir quién consultó, qué se cotizó, para qué obra, quién sigue la atención y qué falta confirmar. No hay aceptación, pedido, reserva, factura ni pago ejecutados. Para probar el recorrido se deben anotar resultado obtenido, usuario, entorno y evidencia; actualmente están pendientes.

Fuente: [guía del catálogo sintético](../../datos/pruebas/README.md), [escenario](escenario-crm.md) y [registro de fuentes](../../fuentes/fuentes-negocio.md). El caso de excepción existente utiliza una variante independiente con nombres/IDs por conciliar; no atribuirle la V02 a este caso normal.
