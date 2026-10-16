# Aporte al flujo: lead, oportunidad y cotización

> **Nota de integración:** este documento detalla los atributos comerciales de las etapas `ETP-01` a `ETP-03` y complementa el flujo general y diagrama BPMN documentados en [`escenario-crm.md`](escenario-crm.md).

## 1. Propósito

Aterrizar al contexto de MIGAL la información comercial que debe conservarse desde el interés inicial hasta la cotización, especialmente probabilidad, competencia, seguimiento, resultado parcial, precio, descuento y versionado.

## 2. Lead y calificación

### AS-IS

`[E]` MIGAL recibe consultas mediante mostrador, WhatsApp, llamadas y referidos. En ventas de obra, el maestro puede actuar como intermediario y traer al cliente o la lista de materiales. `[FN-01][FN-02]`

### TO-BE

Un lead debe conservar al menos:

- canal;
- fuente/referido;
- necesidad inicial;
- persona que contactó;
- cliente responsable, si ya se conoce;
- maestro de obra relacionado, si aplica;
- responsable de seguimiento.

No se exige DNI/RUC como condición universal para registrar un lead.

## 3. Oportunidad

Una oportunidad representa un interés suficientemente concreto como para justificar seguimiento comercial.

### 3.1. Señales para calificar

`[I]` Para MIGAL son señales razonables de intención:

- existe una obra activa o necesidad concreta;
- hay lista de productos o cantidades aproximadas;
- se identifica al decisor o responsable del pago;
- el cliente consulta entrega, descuento o crédito;
- existe un maestro de obra que coordina activamente;
- se solicita una cotización extensa.

Estas señales no garantizan la compra.

### 3.2. Probabilidad

`[TO-BE]` Se propone una escala cualitativa:

| Probabilidad | Criterio orientativo |
|---|---|
| Baja | Interés general, información incompleta o sin decisión próxima |
| Media | Necesidad concreta y productos identificados, pero aún compara alternativas |
| Alta | Obra activa, lista concreta, decisor/maestro identificado y negociación de condiciones o entrega |

`[I]` Se evita usar porcentajes porque MIGAL no dispone de datos históricos calibrados que permitan defender una probabilidad numérica.

### 3.3. Competidores

`[E][AS-IS]` Existen competidores cercanos y los clientes/maestros pueden comunicar que encontraron mejores precios en otras ferreterías. `[FN-02]`

`[TO-BE]` No es obligatorio registrar el nombre del competidor. Puede conservarse:

- referencia competitiva: sí/no;
- competidor conocido, si el cliente lo menciona;
- producto/línea afectada;
- condición comunicada: precio, disponibilidad, flete u otra.

## 4. Seguimiento: próxima acción

`[TO-BE]` Una oportunidad abierta debe poder registrar:

- próxima acción;
- fecha prevista;
- responsable;
- observación breve.

Ejemplos:

- confirmar si el dueño de obra aprobó la cotización;
- consultar si necesita actualización de precio;
- confirmar disponibilidad con proveedor antes de responder;
- hacer seguimiento de una lista enviada.

No se fija una periodicidad rígida.

## 5. Cotización

### 5.1. AS-IS

- `[E]` Se utiliza principalmente para listas extensas y obras. `[FN-01]`
- `[E]` Puede elaborarse en talonario de notas de venta y entregarse mediante copia o fotografía por WhatsApp. `[FN-01]`
- `[E]` Registra principalmente cantidad, producto y precio; la identificación del cliente no siempre es completa. `[FN-01][FN-02]`
- `[E]` No existe una vigencia fija formal. Si el cliente no ha pagado y cambia el costo, el precio puede actualizarse. Una vez realizado el pago, se respeta el precio acordado. `[FN-01][FN-02]`

### 5.2. Versionado propuesto

`[TO-BE]` Cada nueva emisión derivada de un cambio relevante se conserva como una versión:

```text
COT-001-V01 → propuesta inicial
COT-001-V02 → actualización por cambio de precio / negociación
COT-001-V03 → otra revisión, si corresponde
```

La versión anterior no se elimina; permite reconstruir qué se ofreció y por qué cambió.

### 5.3. Precio y descuento

Por línea se propone conservar:

- producto;
- cantidad;
- precio de referencia;
- precio ofrecido;
- diferencia concedida, si existe;
- motivo;
- autorizador, cuando corresponda.

No se propone un porcentaje máximo fijo sin validación de los propietarios.

### 5.4. Vigencia

`[TO-BE]` En lugar de inventar “3 días de vigencia”, la cotización puede declarar una condición coherente con la práctica real:

> **Precio sujeto a actualización mientras no exista confirmación/pago, cuando cambien costos o referencias comerciales.**

Si el equipo posteriormente decide formalizar un plazo concreto, debe tratarse como una política TO-BE validada, no como hecho actual.

## 6. Resultado de la oportunidad

Para representar la realidad de compras de obra se propone distinguir:

- **Ganada total:** el cliente compra toda o prácticamente toda la propuesta acordada en MIGAL.
- **Ganada parcial:** el cliente compra una parte en MIGAL y otra parte no se adjudica.
- **Perdida:** no se concreta compra asociada a la oportunidad.

`[I]` La categoría **ganada parcial** es útil porque un cliente puede distribuir productos entre varias ferreterías según precio, disponibilidad u otras condiciones.

### Motivos de no adjudicación / pérdida

- precio de competencia;
- falta de disponibilidad;
- condición de flete o entrega;
- crédito no concedido;
- necesidad cancelada o modificada;
- cliente sin respuesta;
- compra parcial en otra ferretería;
- otro motivo documentado.

## 7. Frontera de alcance

El flujo de este documento termina en la **propuesta comercial/cotización** y su análisis. La aceptación no implica que este documento diseñe el pedido ERP ni la ejecución operativa posterior.
