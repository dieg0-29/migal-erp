# Caso de análisis — Escenario normal y excepción prioritaria

**Proyecto:** Ferre & Inversiones MIGAL  
**Incremento:** PC2 v2.1  
**Responsable:** Diego Alonso Pinedo Aponte
**Alcance:** CRM previo al pedido confirmado
**Datos:** simulados `[SIM]`, tomados del [catálogo sintético CRM](../../datos/pruebas/catalogos-crm-sinteticos-v2.xlsx); no ejecutados en Odoo.

## 1. Propósito

Presentar, en el formato que exige la rúbrica, un escenario normal y una excepción prioritaria del tramo comercial de MIGAL. Para cada uno se identifica la decisión, el responsable principal, la evidencia esperada, el impacto para el cliente y la respuesta propuesta.

Los dos casos usan registros existentes del catálogo sintético, para que cualquier revisor pueda comprobar cada dato por su identificador:

| Caso | Oportunidad | Cotización | Decisión registrada |
|---|---|---|---|
| Normal | `OPP-SIM-001` | `COT-SIM-001-V01` | Ninguna excepción de precio |
| Excepción prioritaria | `OPP-SIM-002` | `COT-SIM-002-V01` → `V02` | `DEC-SIM-001` (descuento por competencia) |

## 2. Contexto común del negocio

- `[E][AS-IS]` En las ventas de obra intervienen tres actores: MIGAL, el maestro de obra y el dueño de la obra. El maestro trae al cliente, prepara la lista de materiales y recomienda productos; el dueño revisa precios, autoriza y paga. `[FN-01][FN-02]`
- `[E][AS-IS]` Las consultas llegan por mostrador, WhatsApp, llamadas y referidos de maestros. `[FN-01]`
- `[E][AS-IS]` No existe vigencia fija formal de la cotización: si el cliente no ha pagado y cambia el costo, el precio puede actualizarse. `[FN-01][FN-02]`
- `[E][AS-IS]` No existe un porcentaje máximo formal de descuento; ambos propietarios pueden autorizar ajustes. `[FN-01][FN-02]`
- `[E][AS-IS]` En cemento y fierro el margen es menor y el precio está condicionado por el mercado. `[FN-01]`

Las reglas aplicadas provienen del [catálogo RN/EXC](decisiones-comerciales.md#8-catálogo-central-de-reglas-de-negocio-previas-al-pedido-d02--matriz-rn): `RN-02` (próxima acción obligatoria), `RN-03` (precio de lista sujeto a actualización), `RN-04` (versionado de cotizaciones), `RN-05` (promesa de disponibilidad), `RN-06` (condición de facturación prevista) y `EXC-01` (igualar competencia).

## 3. Escenario normal — Lista de obra referida por maestro

El caso distingue los tres conceptos de origen: canal (WhatsApp), fuente (referido maestro) y campaña (ninguna). Si el maestro hubiera recibido la canasta navideña `CAM-03`, la campaña seguiría vacía: la canasta favorece la relación, pero no causa la consulta.

### 3.1. Datos

| Objeto CRM | Valor del catálogo | Rol en el caso |
|---|---|---|
| Cuenta | `CLI-SIM-001 · Cliente Obra Alfa` (Obra) | Responsable económico |
| Contacto decisor | `CON-SIM-001 · Responsable` | Dueño de obra: aprueba y paga |
| Contacto operativo | `CON-SIM-002 · Maestro` | Maestro de obra: envía la lista |
| Dirección | `DIR-SIM-001 · Obra Alfa` (San Martín de Porres) | Contexto de destino, no orden de entrega |
| Fuente | Referido maestro | `[E]` |
| Canal | WhatsApp | `[SIM]` supuesto del recorrido |
| Campaña | Ninguna: el cliente llegó por referencia del maestro, no por una iniciativa de MIGAL | Ver [catálogo de campañas](cuenta-contacto-canales.md#53-catálogo-de-campañas) |
| Oportunidad | `OPP-SIM-001 · Lista completa para obra` · probabilidad **Alta** · responsable **Propietaria** | Resultado: **Abierta** |
| Cotización | `COT-SIM-001-V01` · estado *En revisión* · comprobante previsto *Por definir* | — |
| Próxima acción | Confirmar aprobación del responsable · 17/10/2026 · Propietaria | `RN-02` |

| Línea | Producto | Cantidad | Precio de referencia | Precio ofrecido | Importe |
|---|---|---:|---:|---:|---:|
| 1 | `PRD-SIM-001` Cemento | 100 bolsas | S/ 30.00 | S/ 30.00 | S/ 3,000.00 |
| 2 | `PRD-SIM-002` Fierro | 40 unidades | S/ 40.00 | S/ 40.00 | S/ 1,600.00 |
| 3 | `PRD-SIM-003` Tubería PVC | 20 unidades | S/ 20.00 | S/ 20.00 | S/ 400.00 |
| | | | | **Suma de líneas** | **S/ 5,000.00** |

La suma no incluye impuestos, flete ni descuentos y no se presenta como total fiscal.

### 3.2. Recorrido

| Paso | Etapa | Qué ocurre | Quién |
|---|---|---|---|
| 1 | Lead | El maestro envía la lista; se busca la cuenta existente y se registra la interacción. | Quien atiende |
| 2 | Calificación | Obra activa, lista concreta y decisor identificado → probabilidad Alta. Se vinculan ambos contactos con su rol y la dirección de obra. | Quien atiende |
| 3 | Cotización | Se prepara V01 con precio de lista, sin ajustes (`RN-03`). | Propietaria |
| 4 | Promesa | Si el cliente pide fecha, se registra como **pendiente de comprobación** con responsable; no se mueve stock (`RN-05`). | Propietaria |
| 5 | Comprobante | Se registra comprobante previsto *Por definir*; no se exige RUC para cotizar (`RN-06`). | Quien atiende |
| 6 | Seguimiento | Se fija la próxima acción para confirmar la aprobación del dueño de obra (`RN-02`). | Propietaria |

### 3.3. Ficha de análisis

| Elemento | Escenario normal |
|---|---|
| **Decisión** | Cotizar a precio de lista sin ajuste y asignar el seguimiento hasta que el dueño de obra apruebe. |
| **Responsable principal** | Propietaria, responsable comercial de la oportunidad. |
| **Evidencia esperada** | Oportunidad con fuente, necesidad, probabilidad y ambos contactos con su rol; `COT-SIM-001-V01` con precio de referencia igual al ofrecido; próxima acción con fecha y responsable; promesa y comprobante registrados como pendientes. |
| **Impacto para el cliente** | El dueño de obra recibe por escrito lo mismo que le transmite el maestro; cualquier persona de MIGAL puede responder sobre la cotización sin depender de la memoria de una sola persona. |
| **Respuesta propuesta** | Mantener V01, dar seguimiento el 17/10/2026 y registrar el resultado (ganada, ganada parcial o perdida) cuando el dueño decida. |

**Observación:** el catálogo marca `competencia_referencia = Sí` en `OPP-SIM-001`, pero no registra una solicitud de ajuste. Por eso el caso se trata como normal: hay comparación de precios, pero no decisión excepcional.

## 4. Excepción prioritaria — Presión de precio por competencia

### 4.1. Por qué es la excepción prioritaria

- Afecta directamente al margen en los productos donde MIGAL tiene menos holgura (cemento y fierro). `[E][FN-01]`
- Hoy depende del criterio de los propietarios y no deja rastro de qué se concedió ni por qué. `[E][FN-02]`
- Permite sustentar la decisión de descuento excepcional que exige la rúbrica sin inventar una política porcentual.

### 4.2. Datos

| Objeto CRM | Valor del catálogo |
|---|---|
| Cuenta | `CLI-SIM-002 · Cliente Obra Beta` (Obra) |
| Contacto decisor | `CON-SIM-003 · Responsable Beta` (dueño de obra) |
| Contacto operativo | `CON-SIM-004 · Maestro Beta` (maestro de obra) |
| Canal / fuente / campaña | WhatsApp / no registrada `[ND]` / ninguna |
| Oportunidad | `OPP-SIM-002 · Cemento y fierro para avance de obra` · probabilidad **Alta** · competencia **Sí** · responsable **Dueño** |
| Decisión | `DEC-SIM-001` · Descuento · *Cliente comunica mejor precio de competencia* · **Ajuste autorizado** · Dueño · 16/10/2026 |
| Resultado | **Ganada parcial** · motivo: *Precio de competencia en fierro* |

| Línea | Producto | Cant. | V01 (referencia) | V02 (ofrecido) | Motivo V02 | Autorizó | Resultado de línea |
|---|---|---:|---:|---:|---|---|---|
| 1 | `PRD-SIM-001` Cemento | 80 | S/ 30.20 | S/ 30.00 | Volumen | Dueño | Adjudicada |
| 2 | `PRD-SIM-002` Fierro | 60 | S/ 40.50 | S/ 40.10 | Competencia | Dueño | No adjudicada |
| | **Suma** | | **S/ 4,846.00** | **S/ 4,806.00** | | | |

Beneficio concedido en V02: S/ 16.00 en cemento y S/ 24.00 en fierro (S/ 40.00 en total). Importe adjudicado a MIGAL: S/ 2,400.00 (cemento).

### 4.3. Punto de ramificación respecto del caso normal

Ambos casos siguen el mismo recorrido hasta la emisión de V01. La excepción se activa cuando el maestro informa que otra ferretería ofrece un precio menor y pide mejorarlo (`EXC-01`). En el caso normal no hay esa solicitud y V01 se mantiene.

### 4.4. Opciones evaluadas

| Opción | Descripción | Evaluación |
|---|---|---|
| A | El propietario autoriza un ajuste y se emite V02 conservando V01 | **Elegida** en el catálogo (`DEC-SIM-001`) |
| B | Mantener V01 y aceptar perder la línea | Válida si el margen no lo permite |
| C | Quien atiende rebaja el precio sin autorización | Descartada: es el riesgo AS-IS de vender cerca del costo |

### 4.5. Ficha de análisis

| Elemento | Excepción prioritaria |
|---|---|
| **Decisión** | Ajustar el precio de cemento (por volumen) y de fierro (por competencia) en una nueva versión. |
| **Responsable principal** | Dueño, como responsable de la oportunidad. Cualquiera de los propietarios puede autorizar. `[E]` |
| **Información considerada** | Precio de referencia, cantidad, mezcla de productos, relación con el maestro, condición de entrega y precio comunicado por la competencia. |
| **Evidencia esperada** | V01 conservada; V02 con precio de referencia, precio ofrecido, diferencia, motivo y autorizador por línea; decisión `DEC-SIM-001` con fecha; resultado y motivo de no adjudicación. |
| **Impacto para el cliente** | Recibe una respuesta explicable y no arbitraria; el precio no depende de quién lo atienda; puede decidir dónde comprar cada línea con información clara. |
| **Respuesta propuesta** | Emitir V02 con el ajuste autorizado. El cliente compra el cemento en MIGAL y el fierro en otra ferretería: la oportunidad se registra como **Ganada parcial** con motivo *Precio de competencia en fierro*, sin clasificarla como perdida. |

### 4.6. Aprendizaje del caso

`[I]` El ajuste de S/ 0.40 por unidad en fierro no bastó para retener la línea. Registrar el motivo de no adjudicación permite a los propietarios revisar, con datos y no solo con memoria, en qué productos la competencia gana por precio.

## 5. Frontera CRM–ERP en ambos casos

| CRM conserva | ERP compromete y ejecuta (fuera de PC2) |
|---|---|
| Cuenta, contactos y su rol, dirección de obra, fuente y canal, necesidad, probabilidad, competencia, versiones de cotización, decisiones con motivo y autorizador, promesa comunicada, comprobante previsto, resultado y motivo | Confirmación del pedido, reserva de stock, despacho, emisión del comprobante en KeyFacil y cobro |

La frontera se ubica en la confirmación de la cotización, según [ADR-004](../../arquitectura/decisiones/ADR-004-odoo-community-fronteras-crm-erp.md) y el [diagrama de componentes CRM](../../arquitectura/vistas/c4/render/componentes/crm.png).

## 6. Clasificación de afirmaciones

| Afirmación | Clasificación |
|---|---|
| Maestro refiere y envía listas; dueño revisa y paga | `[E][AS-IS]` |
| No existe vigencia fija ni porcentaje máximo de descuento | `[E][AS-IS]` |
| Ambos propietarios pueden autorizar ajustes | `[E][AS-IS]` |
| Registrar versión, motivo, autorizador y resultado parcial | `[TO-BE]` |
| Probabilidad cualitativa Baja/Media/Alta | `[I][TO-BE]` |
| Nombres, cantidades, precios y fechas | `[SIM]` |

## 7. Límites y pendientes

- El caso no prueba pedido, reserva de inventario, entrega, emisión de comprobante ni cobro.
- No se ejecutó en una instancia de Odoo; los estados y modelos son conceptuales.
- [`caso-excepcion.md`](caso-excepcion.md) presenta una variante ilustrativa (S/ 40.00 → S/ 39.70 sobre `OPP-SIM-001`) que no figura en el catálogo. Debe conciliarse con este documento o declararse como variante.

## Fuentes

- `FN-01` Monografía 1 – Grupo 1 – SI704V (acceso 15/10/2026).
- `FN-02` Aclaraciones de campo registradas por Brenda Mirano (acceso 16/10/2026).
- [Catálogo sintético CRM](../../datos/pruebas/README.md), hojas *Clientes*, *Contactos*, *Oportunidades*, *Cotizaciones*, *Cotizaciones_Detalle* y *Decisiones_Comerciales*.
- [Decisiones comerciales](decisiones-comerciales.md), [caso normal](caso-normal.md) y [caso de excepción](caso-excepcion.md).
