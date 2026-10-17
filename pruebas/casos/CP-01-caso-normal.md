# CP-01: Caso normal — cotización de materiales para obra

## 1. Metadatos

* **Fecha:** 17/10/2026
* **Versión:** 0.1
* **Autores:** Diego Pinedo
* **Proceso:** [Flujo comercial](../../procesos/comercial-crm/flujo-comercial.md)
* **Estado:** Por ejecutar en Odoo

## 2. Objetivo

Comprobar que se puede recuperar el contexto del cliente, preparar una cotización y registrar el seguimiento sin excepción de precio, con datos del [catálogo sintético](../../datos/pruebas/README.md).

## 3. Datos de entrada `[SIM]`

| Objeto | Valor del catálogo | Rol en el caso |
|---|---|---|
| Cuenta | `CLI-SIM-001` · Rosa Elena Huamán Salcedo | Responsable económica |
| Contacto decisor | `CON-SIM-001` · Rosa Elena Huamán Salcedo | Dueña de obra: aprueba y paga |
| Contacto operativo | `CON-SIM-002` · Luis Fernando Salcedo Poma | Maestro de obra: envía la lista |
| Dirección | `DIR-SIM-001` · Ampliación tercer piso — familia Huamán (San Martín de Porres) | Contexto de la obra, no orden de entrega |
| Canal / fuente / campaña | WhatsApp `[SIM]` / referido maestro / ninguna | La consulta la causó el maestro, no una campaña |
| Oportunidad | `OPP-SIM-001` · Materiales para tercer piso · probabilidad Alta · responsable R-PRO | Abierta |
| Cotización | `COT-SIM-001-V01` · En revisión · comprobante previsto *Por definir* | — |

| Línea | Producto | Cantidad | Precio de referencia | Precio ofrecido | Importe |
|---|---|---:|---:|---:|---:|
| 1 | `PRD-SIM-001` Cemento | 100 bolsas | S/ 31.00 | S/ 31.00 | S/ 3,100.00 |
| 2 | `PRD-SIM-002` Fierro | 40 unidades | S/ 40.50 | S/ 40.50 | S/ 1,620.00 |
| 3 | `PRD-SIM-003` Tubería PVC | 20 unidades | S/ 20.00 | S/ 20.00 | S/ 400.00 |
| | | | | **Suma de líneas** | **S/ 5,120.00** |

La suma no incluye impuestos, flete ni descuentos y no es un total fiscal.

## 4. Precondiciones

* Cuenta, contactos y dirección existen en el catálogo.
* R-ATN dispone de la lista; R-PRO revisa precios. No se presupone ningún permiso técnico configurado.

## 5. Pasos

| Paso | Etapa | Acción | Actor | Regla | Evidencia esperada |
|---|---|---|---|---|---|
| 1 | Lead | El maestro envía la lista; se busca la cuenta existente y se registra la interacción | R-ATN | RN-01 | Interacción vinculada a `CLI-SIM-001` y `CON-SIM-002`, sin duplicar la cuenta |
| 2 | Calificación | Obra activa, lista concreta y decisor identificado: probabilidad Alta; se vinculan ambos contactos y la dirección | R-ATN | RN-02 | Oportunidad con fuente, necesidad, probabilidad y contactos con su rol |
| 3 | Cotización | Se prepara V01 con precio de lista, sin ajustes | R-PRO | RN-03 | Líneas y versión identificables; referencia igual a ofrecido |
| 4 | Promesa | Si el cliente pide fecha, se registra como pendiente de comprobación; no se mueve stock | R-PRO | RN-05 | Condición y responsable |
| 5 | Comprobante | Comprobante previsto *Por definir*; no se exige RUC para cotizar | R-ATN | RN-06 | Campo registrado |
| 6 | Seguimiento | Próxima acción el 17/10/2026 para confirmar la aprobación de la dueña de obra | R-PRO | RN-02 | Acción, fecha y responsable |

## 6. Resultado esperado

| Elemento | Resultado |
|---|---|
| Decisión | Cotizar a precio de lista sin ajuste y dar seguimiento hasta que la dueña de obra apruebe |
| Responsable | R-PRO (propietaria, responsable de la oportunidad) |
| Impacto para el cliente | La dueña de obra recibe por escrito lo mismo que le transmite el maestro; cualquier persona de MIGAL puede responder sin depender de la memoria de una sola persona |
| Respuesta | Mantener V01 y registrar el resultado (ganada, ganada parcial o perdida) cuando la dueña decida |

`[I]` El catálogo marca `competencia_referencia = Sí` en `OPP-SIM-001`, pero no registra una solicitud de ajuste; por eso el caso es normal.

## 7. Resultado obtenido

Pendiente de ejecución. Registrar entorno, usuario, fecha, resultado y evidencia en `pruebas/resultados/`.

## 8. Límites

No prueba pedido, reserva, entrega, comprobante ni cobro. La auditoría de su cadena completa está en el [plan de trazabilidad](../../datos/trazabilidad/plan-trazabilidad-auditoria.md).

## 9. Historial de cambios

| Versión | Fecha | Autor | Cambio |
|---|---|---|---|
| 0.1 | 17/10/2026 | Diego Pinedo | Versión inicial; reúne el caso normal y su ficha de análisis |
