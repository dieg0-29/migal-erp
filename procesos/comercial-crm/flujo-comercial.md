# Flujo comercial: de la consulta a la cotización aceptada

## 1. Metadatos

* **Fecha:** 17/10/2026
* **Versión:** 0.1
* **Autores:** Alejandro Flores
* **Sistema:** CRM (Odoo 18 Community)

## 2. Propósito

`[E][AS-IS]` Hoy las consultas que no se cierran de inmediato se pierden entre WhatsApp, el mostrador y la memoria de los propietarios; los precios y márgenes dependen de una sola persona y no hay un registro de qué se cotizó ni por qué. `[FN-01][FN-02]`

El flujo propuesto centraliza toda intención de compra en el CRM, permite priorizar el seguimiento y conserva cada cotización con su versión, precio y decisión, sin exigir al cliente datos que la consulta no necesita.

## 3. Inicio y fin

* **Inicio:** primer contacto, consulta o lista de materiales recibida por cualquier canal.
* **Fin:** cotización aceptada, que pasa al ERP como pedido ([INT-01](../../arquitectura/integraciones/INT-01-CRM-ERP.md), F-02); o oportunidad cerrada como ganada parcial o perdida, con su motivo.

## 4. Actores

| Perfil | Participación |
|---|---|
| R-ATN | Registra consultas, leads, oportunidades, cotizaciones y seguimiento |
| R-PRO | Decide excepciones de precio, promesas de disponibilidad crítica y condiciones especiales |
| Cliente, dueño de obra o maestro de obra | Consulta, negocia y acepta; el maestro puede preparar la lista y el dueño suele pagar |

## 5. Entradas y salidas

| Entradas | Salidas |
|---|---|
| Consulta por mostrador, WhatsApp, teléfono o referido; lista de materiales; catálogo y lista de precios | Lead, oportunidad calificada, cotización versionada, decisiones registradas, resultado comercial |

Canales, fuentes y campañas: ver [cuenta, contacto y canales](cuenta-contacto-canales.md). Campos: ver [diccionario de datos](../../datos/diccionario-datos.md).

## 6. Flujo

![Diagrama BPMN del proceso comercial](render/flujo-comercial.png)

Fuente editable: [`fuentes/flujo-comercial.bpm`](fuentes/flujo-comercial.bpm). Eventos de negocio de cada etapa: [INT-01](../../arquitectura/integraciones/INT-01-CRM-ERP.md), §4.

| Paso | Etapa | Actividad | Actor | Regla | Evidencia |
|---|---|---|---|---|---|
| 1 | ETP-01 Nuevo (lead) | Recibir la consulta, buscar la cuenta o contacto existente y registrar el lead con canal, fuente, necesidad inicial y responsable de seguimiento | R-ATN | RN-01 | Lead con identificador; no se exige DNI/RUC |
| 2 | ETP-02 Calificado (oportunidad) | Si hay una necesidad concreta, crear la oportunidad: cuenta y contactos con su rol, obra o dirección, probabilidad, competencia y próxima acción | R-ATN | RN-02 | Oportunidad con responsable y próxima acción |
| 3 | ETP-03 Propuesta (cotización) | Elaborar la cotización con productos del catálogo, precios de la lista vigente y comprobante previsto | R-ATN | RN-03, RN-06 | Cotización V01 con líneas, precios y comprobante previsto |
| 4 | ETP-03 | Si el cliente pide fecha o disponibilidad, confirmar con quien tenga autorización antes de prometer | R-PRO | RN-05 | Promesa con condición (confirmada, pendiente o condicionada) y responsable |
| 5 | ETP-03 | Si el cliente pide mejor precio, decidir la excepción y emitir una nueva versión | R-PRO | EXC-01, RN-04 | Nueva versión con precio de referencia, ofrecido, motivo y autorizador |
| 6 | Seguimiento | Comunicar la cotización y dar seguimiento según la próxima acción | R-ATN | RN-02 | Registro de envío, respuesta y siguiente acción |
| 7 | Cierre | Registrar el resultado: aceptada (pasa al ERP), ganada parcial o perdida con motivo | R-ATN | RN-08 | Versión aceptada, quién aceptó y cuándo; o motivo de no adjudicación |

### 6.1. Criterios por etapa

**Señales para calificar (paso 2).** `[I]` Obra activa o necesidad concreta; lista de productos o cantidades aproximadas; decisor o responsable del pago identificado; consulta de entrega, descuento o crédito; maestro de obra que coordina activamente; pedido de cotización extensa. Estas señales no garantizan la compra.

**Probabilidad.** `[TO-BE]` Escala cualitativa, porque MIGAL no tiene datos históricos para calibrar porcentajes:

| Probabilidad | Criterio orientativo |
|---|---|
| Baja | Interés general, información incompleta o sin decisión próxima |
| Media | Necesidad concreta y productos identificados, pero aún compara alternativas |
| Alta | Obra activa, lista concreta, decisor identificado y negociación de condiciones o entrega |

**Competencia.** No es obligatorio registrar el nombre del competidor. Se conserva si hubo referencia competitiva, el competidor si el cliente lo menciona, la línea afectada y la condición comunicada (precio, disponibilidad, flete u otra).

**Versionado.** Cada cambio relevante genera una versión nueva y la anterior se conserva: `COT-SIM-001-V01` → `COT-SIM-001-V02`.

**Vigencia.** `[E][AS-IS]` No existe una vigencia fija: mientras no haya confirmación o pago, el precio puede actualizarse si cambian los costos; una vez pagado, se respeta. La cotización declara: *precio sujeto a actualización mientras no exista confirmación o pago*. Un plazo fijo solo se usará si los propietarios lo aprueban.

**Precio por línea.** Producto, cantidad, precio de referencia, precio ofrecido, diferencia, motivo y autorizador cuando corresponda. No se propone un porcentaje máximo de descuento sin validación de los propietarios ([precios](../../datos/maestros/precios.md)).

## 7. Excepciones

| Situación | Tratamiento | Regla |
|---|---|---|
| Contacto inválido | Lead descartado con motivo, sin crear cuenta de cliente | — |
| Necesidad no calificada | El lead permanece en "Nuevo" o se descarta | RN-02 |
| Mejor precio de la competencia | Decide R-PRO; nueva versión con motivo y autorizador | EXC-01 |
| Stock registrado distinto del físico | No comprometer el faltante; avisar a almacén y ofrecer sustituto o dejar pendiente | EXC-02 |
| Cambio de costos antes de la confirmación | Nueva versión con el precio actualizado | RN-03, RN-04 |
| Compra repartida entre ferreterías | Resultado "Ganada parcial", con motivo de la línea no adjudicada | — |

Motivos de no adjudicación: precio de la competencia, falta de disponibilidad, flete o entrega, crédito no concedido, necesidad cancelada, cliente sin respuesta, compra parcial en otra ferretería u otro motivo documentado.

## 8. Indicadores

Ver [indicadores O2C](../o2c/indicadores.md), O2C-K-01 a O2C-K-04, que cubren seguimiento, trazabilidad de cotizaciones, tiempo de respuesta y excepciones.

## 9. Pendientes de validación

* Comprobar en Odoo cómo se representan las etapas, el versionado de cotizaciones y la conversión de oportunidad a cotización; ningún bloqueo (por ejemplo, impedir cotizar sin stock) se da por hecho sin probarlo.
* Validar con los propietarios la escala de probabilidad y los motivos de no adjudicación.

## 10. Historial de cambios

| Versión | Fecha | Autor | Cambio |
|---|---|---|---|
| 0.1 | 17/10/2026 | Alejandro Flores | Versión inicial; reúne el escenario CRM y el detalle de lead, oportunidad y cotización |

Fuentes: [fuentes del negocio](../../fuentes/fuentes-negocio.md) (FN-01, FN-02).
