# Catálogo de reglas de negocio

## 1. Metadatos

* **Fecha:** 17/10/2026
* **Versión:** 0.1
* **Autores:** Alejandro Flores
* **Custodio:** R-PRO

## 2. Propósito

Este catálogo es la **única numeración** de reglas de negocio (RN), sus controles (CT) y las excepciones (EXC) de todos los procesos. Los flujos, casos de prueba, la [matriz de trazabilidad](../datos/trazabilidad/plan-trazabilidad-auditoria.md) y las integraciones citan estos códigos. Cada control CT-nn verifica la regla RN-nn del mismo número.

Las reglas son propuestas funcionales: que una regla exista no significa que Odoo la haga cumplir automáticamente. Su aplicación se comprueba en los casos de prueba.

## 3. Reglas del proceso comercial (CRM)

Detalle de las decisiones que originan estas reglas: [decisiones comerciales](comercial-crm/decisiones-comerciales.md).

| ID | Regla | Etapa | Motivo | Sistema | Control | Consecuencia si se viola | Responsable |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **RN-01** | **Control de Duplicados:** Un cliente o "lead" no puede registrarse dos veces con el mismo celular o nombre clave. | ETP-01: Nuevo | Evitar bases de datos sucias y que dos vendedores atiendan al mismo cliente ofreciendo condiciones distintas. | CRM | CT-01 | Sistema advierte coincidencia y sugiere fusionar con la ficha existente. | R-ATN |
| **RN-02** | **Próxima Acción Obligatoria:** Toda Oportunidad perfilada debe tener asignada una fecha o tarea de seguimiento. | ETP-02: Calificado | Evitar que las obras o ventas importantes "se enfríen" por olvido del vendedor. | CRM | CT-02 | El sistema marca la oportunidad en alerta de abandono tras permanecer sin seguimiento programado. | R-ATN |
| **RN-03** | **Precios de Lista Vigente:** Los precios unitarios en la cotización deben extraerse de la base de datos y están sujetos a actualización mientras no exista un pago o confirmación formal. | ETP-03: Propuesta | Proteger el margen frente a la volatilidad del costo de agregados y fierros. | ERP | CT-03 | El sistema obliga a actualizar precios si cambian los costos antes de la confirmación/pago. | R-PRO |
| **RN-04** | **Versionado de Cotizaciones:** Si el cliente solicita cambios en cantidades o productos tras recibir una proforma, se crea una nueva "versión" de la cotización, sin sobrescribir ni eliminar la original. | ETP-03: Propuesta | Mantener un historial auditable de la negociación para entender qué productos descartó el cliente. | ERP/CRM | CT-04 | Imposibilidad de eliminar cotizaciones enviadas; solo se permite "Clonar/Versionar". | R-ATN |
| **RN-05** | **Promesa de Disponibilidad:** Solo el personal autorizado (R-ATN/R-PRO) puede confirmar al cliente la disponibilidad física de un material crítico (ej. Cemento) basándose en la consulta del sistema y condiciones operativas. | ETP-03: Propuesta | Evitar que asistentes o personal no autorizado prometan despachos imposibles de cumplir. | CRM/ERP | CT-05 | Restricción de compromiso de entrega según el rol del usuario. | R-ATN / R-PRO |
| **RN-06** | **Condición de Facturación Prevista:** Antes de emitir la cotización, se debe consultar si la eventual compra requerirá Boleta o Factura (aunque no se exija RUC en ese instante). | ETP-03: Propuesta | Preparar administrativamente el cierre del pedido y anticipar si se tratará de una cuenta empresa o persona natural. | CRM | CT-06 | Campo "Tipo de Comprobante Esperado" registrado como `Boleta`, `Factura` o `Por Definir`. | R-ATN |

## 4. Reglas de Order to Cash (ERP)

Aplican desde que la cotización aceptada pasa al ERP ([INT-01](../arquitectura/integraciones/INT-01-CRM-ERP.md), F-02).

| ID | Regla | Etapa | Motivo | Sistema | Control | Consecuencia si se viola | Responsable |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **RN-07** | **Identificación según la operación:** El cliente se identifica con los datos que exija la operación (entrega, comprobante) y se conserva el origen de cada dato. | Pedido | Evitar exigir datos innecesarios y, a la vez, emitir comprobantes con identidad correcta. | CRM/ERP | CT-07 | Pedido o comprobante con identidad incompleta o sin origen trazable. | R-ATN / R-PRO |
| **RN-08** | **Aceptación vinculada:** El pedido solo se crea desde una cotización aceptada, conservando la versión aceptada. | Pedido | Asegurar que lo ejecutado coincide con lo acordado. | ERP | CT-08 | Pedido sin aceptación o con condiciones distintas a las cotizadas. | R-ATN / R-PRO |
| **RN-09** | **Reserva por ubicación:** El pedido se relaciona con la disponibilidad y reserva de cada punto físico (Tienda, Almacén 1, Almacén 2). | Reserva | Evitar comprometer stock inexistente o de otra ubicación. | ERP | CT-09 | Promesas incumplidas y descuadre entre ubicaciones. | R-ALM / R-PRO |
| **RN-10** | **Entrega real:** Se registran las cantidades realmente entregadas y las diferencias físicas. | Entrega | Mantener visible lo pendiente y la exactitud del inventario. | ERP | CT-10 | Saldos pendientes ocultos e inventario inexacto. | R-ALM |
| **RN-11** | **Conciliación con KeyFacil:** La referencia del comprobante emitido en KeyFacil se concilia con el pedido y sus importes. | Comprobante | Evitar doble emisión o diferencias entre lo vendido y lo facturado. | ERP / KeyFacil | CT-11 | Descuadres fiscales y comprobantes sin operación de origen. | R-FAC |
| **RN-12** | **Cobro documentado:** Cada cobro se registra con soporte verificable y saldo resultante. | Cobro | Conocer lo pendiente por cobrar. | ERP | CT-12 | Saldos incorrectos y cobros sin respaldo. | R-FAC |
| **RN-13** | **Posventa vinculada:** Todo caso de posventa se relaciona con el pedido de origen. | Posventa | Resolver reclamos con el contexto de la venta. | ERP | CT-13 | Devoluciones o notas sin sustento. | R-ATN / R-PRO |
| **RN-14** | **Cierre verificado:** El pedido se cierra solo con entrega, cobro e incidencias resueltos. | Cierre | Evitar cierres con pendientes. | ERP | CT-14 | Operaciones cerradas con saldos o entregas pendientes. | R-PRO |
| **RN-15** | **Decisión de crédito:** Toda condición de crédito nueva o modificada requiere decisión expresa de un propietario. | Pedido | Evitar financiación no autorizada. | ERP | CT-15 | Ventas a crédito sin respaldo (ver SOD-04). | R-PRO |

## 5. Reglas de Procure to Pay (ERP)

| ID | Regla | Etapa | Evidencia esperada | Sistema | Control | Consecuencia si se viola | Responsable |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **RN-16** | **Toda reposición tiene necesidad identificable.** | P2P | Producto, unidad, cantidad y causa | ERP | CT-16 | Necesidad, recepción o pago sin respaldo verificable. | R-ALM / R-PRO |
| **RN-17** | **Revisar existencias y compras pendientes antes de repetir compra.** | P2P | Referencias consultadas o incertidumbre | ERP | CT-17 | Necesidad, recepción o pago sin respaldo verificable. | R-PRO / R-ALM |
| **RN-18** | **Confirmar proveedor, precio y condiciones antes del compromiso.** | P2P | Oferta y decisión; cambios requieren nueva constancia | ERP | CT-18 | Necesidad, recepción o pago sin respaldo verificable. | R-PRO |
| **RN-19** | **Registrar cantidad real recibida, no copiar cantidad comprada sin contar.** | P2P | Conteo, daños y ubicación | ERP | CT-19 | Necesidad, recepción o pago sin respaldo verificable. | R-ALM |
| **RN-20** | **Diferencias mantienen saldo físico o excepción.** | P2P | Cantidad pendiente y resolución | ERP | CT-20 | Necesidad, recepción o pago sin respaldo verificable. | R-ALM / R-PRO |
| **RN-21** | **Separar recepción de ajuste de inventario.** | P2P | Documento de entrada; ajuste con causa/autorización | ERP | CT-21 | Necesidad, recepción o pago sin respaldo verificable. | R-ALM / R-PRO |
| **RN-22** | **Cotejar compra, recepción y documento antes de cerrar obligación.** | P2P | Coincidencias y discrepancias | ERP | CT-22 | Necesidad, recepción o pago sin respaldo verificable. | R-FAC / R-PRO |
| **RN-23** | **Verificar pago y aplicación sin duplicidades.** | P2P | Soporte, monto, obligación y saldo | ERP | CT-23 | Necesidad, recepción o pago sin respaldo verificable. | R-PRO |
| **RN-24** | **Mantener trazabilidad de anulaciones/devoluciones.** | P2P | Motivo, decisión y efecto físico/económico | ERP | CT-24 | Necesidad, recepción o pago sin respaldo verificable. | R-PRO / R-ALM |
| **RN-25** | **Cerrar con saldo resuelto o excepción documentada.** | P2P | Estado físico y económico separados | ERP | CT-25 | Necesidad, recepción o pago sin respaldo verificable. | R-PRO |

## 6. Excepciones

| ID | Excepción | Tratamiento | Acción en el sistema |
| :--- | :--- | :--- | :--- |
| **EXC-01** | **Excepción de Descuento (Igualar competencia):** Cliente demuestra que otra ferretería tiene un precio menor en un material clave. | La decisión recae exclusivamente en los propietarios. Si el volumen justifica el sacrificio de margen, se aprueba el descuento extraordinario. | Propietario aprueba la excepción en el sistema, generando nueva versión y dejando traza de su usuario. |
| **EXC-02** | **Sin Stock por Desfase (Inventario Fantasma):** El sistema muestra stock para cotizar, pero el vendedor sabe (por conocimiento físico) que el producto está dañado o no hay la cantidad suficiente. | El vendedor no compromete el producto faltante, notifica la discrepancia a almacén y ofrece un sustituto o deja pendiente en la proforma. | Se registra la observación y se levanta alerta de "Ajuste de Inventario" en el ERP. |

## 7. Trazabilidad

| Reglas | Origen | Se verifican en |
| :--- | :--- | :--- |
| RN-01 a RN-06 | [Flujo comercial](comercial-crm/flujo-comercial.md) y [decisiones comerciales](comercial-crm/decisiones-comerciales.md) | [INT-01](../arquitectura/integraciones/INT-01-CRM-ERP.md), [plan de trazabilidad](../datos/trazabilidad/plan-trazabilidad-auditoria.md) (TR-01 a TR-03), [CP-01](../pruebas/casos/CP-01-caso-normal.md) |
| EXC-01 | [Decisiones comerciales](comercial-crm/decisiones-comerciales.md) | SOD-01 del [modelo de autorización](../arquitectura/seguridad/modelo-autorizacion.md), TR-04, [CP-02](../pruebas/casos/CP-02-caso-excepcion.md) |
| EXC-02 | [Decisiones comerciales](comercial-crm/decisiones-comerciales.md) | SOD-03, [CP-02](../pruebas/casos/CP-02-caso-excepcion.md) |
| RN-07 a RN-15 | [Flujo O2C](o2c/flujo.md), [pedido](o2c/pedido.md), [facturación](o2c/facturacion.md) | [Plan de trazabilidad](../datos/trazabilidad/plan-trazabilidad-auditoria.md) (TR-05 a TR-11); casos por definir |
| RN-16 a RN-25 | [Flujo P2P](p2p/flujo.md) | [Eventos y controles P2P](p2p/eventos-controles.md); casos por definir |

## 8. Equivalencias con códigos retirados

Las reglas O2C-R y P2P-R se integraron en este catálogo y ya no se usan.

| Código retirado | Ahora |
| :--- | :--- |
| O2C-R-01 | RN-07 |
| O2C-R-02 | RN-03 y DQ-04 |
| O2C-R-03 | RN-04 |
| O2C-R-04 | EXC-01 |
| O2C-R-05 | RN-05 |
| O2C-R-06 | RN-08 |
| O2C-R-07 | RN-09 y RN-10 |
| O2C-R-08 | RN-11 |
| O2C-R-09 | RN-12 |
| O2C-R-10 | RN-14 |
| P2P-R-01 a P2P-R-10 | RN-16 a RN-25 |

## 9. Historial de cambios

| Versión | Fecha | Autor | Cambio |
|---|---|---|---|
| 0.1 | 17/10/2026 | Alejandro Flores | Versión inicial; reúne las reglas de CRM, O2C y P2P |
