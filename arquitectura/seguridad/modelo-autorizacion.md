# Modelo de autorización y segregación de funciones

## 1. Metadatos

* **Fecha:** 17/10/2026
* **Versión:** 0.1
* **Autores:** Luis Núñez
* **Sistemas involucrados:** CRM y ERP (Odoo 18 Community), KeyFacil (externo)
* **Matriz asociada:** [matriz-permisos.xlsx](matriz-permisos.xlsx)

## 2. Propósito y alcance

Este modelo preserva la integridad de leads, clientes, cotizaciones, pedidos, existencias, comprobantes y registros de negocio de Ferre & Inversiones MIGAL. Las responsabilidades se distribuyen en perfiles funcionales, sin suponer nuevos puestos de trabajo: MIGAL cuenta con dos propietarios y dos trabajadores, por lo que una misma persona puede ejercer varios perfiles, sujeta a controles sobre operaciones incompatibles.

La autorización comprende lead, cliente, cotización, pedido, comprobante, precio, stock, crédito y cobro, posventa y trazas. Odoo 18 Community soporta el CRM y el ERP ([ADR-002](../decisiones/ADR-002-version-y-edicion.md)); KeyFacil conserva la emisión fiscal y WhatsApp funciona como canal de comunicación ([ADR-004](../decisiones/ADR-004-odoo-community-fronteras-crm-erp.md)).

Las autorizaciones son reglas de diseño. Su cumplimiento se acredita mediante pruebas por perfil en la instancia de Odoo.

## 3. Perfiles funcionales

La asignación de cada perfil corresponde a la función desempeñada y conserva la identidad individual del usuario. La segregación se evalúa por operación, aun cuando una misma persona reúna varios perfiles. Los demás documentos del repositorio se refieren a estos perfiles por su código.

| Código | Perfil | Reglas en la matriz | Acceso principal y límite | Asignación en MIGAL |
|---|---|---|---|---|
| R-ATN | Atención comercial | PR-02 | Registrar leads, clientes, cotizaciones y aceptación documentada. No aprueba sus descuentos ni emite o anula comprobantes. | Trabajadores y propietarios |
| R-PRO | Propietario aprobador | PR-04 | Decidir excepciones comerciales, condiciones de crédito y regularizaciones sensibles, y custodiar los datos maestros. No aprueba excepciones que inició; requiere revisión cruzada. | Propietarios |
| R-ALM | Operación de almacén | PR-05 | Registrar recepción, preparación, despacho y diferencias físicas. No aprueba su propio ajuste de inventario ni administra precios. | Trabajadores |
| R-FAC | Facturación y cobro | PR-06 | Registrar número fiscal, cobros y conciliación con KeyFacil. KeyFacil solo lo opera un propietario autorizado; la anulación requiere control independiente. | Propietarios |
| R-TEC | Administración técnica | PR-07 | Administrar usuarios, módulos, grupos y continuidad técnica. Sin facultades comerciales por defecto. | **Pendiente:** MIGAL no tiene personal de TI ([ADR-002](../decisiones/ADR-002-version-y-edicion.md)) |
| R-INT | Cuenta de servicio | PR-08 | Intercambiar datos mínimos con un sistema externo. Sin acceso interactivo, aprobación, precios ni anulaciones. | **Condicional:** se habilita solo si se aprueba una interfaz externa |

Cada regla se identifica como `PR-<perfil>.<objeto>`; por ejemplo, PR-02.03 es el acceso de atención comercial a la cotización. La matriz contiene 60 reglas: seis perfiles por diez objetos.

## 4. Resumen de permisos por objeto

Acciones: V = ver, C = crear, E = editar, A = aprobar, N = anular. «Sí» concede el acceso; «Cond.» lo condiciona a la regla escrita en la matriz; «No» lo deniega; «N/A» indica una acción no pertinente. El alcance de lectura aplica el principio de mínimo privilegio.

| Objeto | R-ATN | R-PRO | R-ALM | R-FAC |
|---|---|---|---|---|
| Lead | V C E · N cond. | V C E · N cond. | Sin acceso | Sin acceso |
| Cliente | V C · E cond. | V C · E A cond. | V cond. (entrega) | V E cond. (datos fiscales) |
| Cotización | V C · E cond. | V C · E A N cond. | V cond. (líneas del pedido) | V cond. |
| Pedido | V C · E A cond. | V C · E A N cond. | V · E cond. (resultado físico) | V · E cond. (referencia fiscal) |
| Comprobante | V cond. (número y estado) | V · C E A N cond. | Sin acceso | V · C E cond. |
| Precio | V | V C E A · N cond. | Sin acceso | V cond. |
| Stock | V | V · E A cond. (ajuste) | V C · E cond. (sin ajustar saldo) | V cond. |
| Crédito y cobro | V cond. (resumen) | V · C E A cond. | Sin acceso | V C · E cond. (no aprueba crédito) |
| Posventa | V C E · N cond. | V C A · E N cond. | V C E cond. | V E cond. |
| Trazas | V cond. (propias) | V | V cond. (propias) | V cond. (a cargo) |

R-TEC no tiene acceso a objetos de negocio; solo consulta trazas para diagnóstico, sin modificarlas. R-INT no tiene acceso mientras no exista una interfaz externa aprobada. El detalle de cada regla, su condición y el riesgo que controla está en la [matriz](matriz-permisos.xlsx).

## 5. Segregación de funciones

| Control | Segregación establecida | Iniciador | Aprobador | Evidencia mínima | Vínculo |
|---|---|---|---|---|---|
| SOD-01 · Precio | El iniciador no aprueba su propia excepción de precio. | R-ATN o R-PRO | Otro R-PRO | Cotización, valores previo y aprobado, motivo, usuario y fecha | [EXC-01](../../procesos/comercial-crm/decisiones-comerciales.md) |
| SOD-02 · Comprobante | La anulación la autoriza un propietario distinto del emisor. | R-FAC | Otro R-PRO | Comprobante original, motivo, decisión y nota o reversión | — |
| SOD-03 · Inventario | Almacén reporta la diferencia; el propietario autoriza; regulariza quien no hizo el conteo. | R-ALM | R-PRO | Conteo, diferencia, movimiento y autorización | [EXC-02](../../procesos/comercial-crm/decisiones-comerciales.md) |
| SOD-04 · Crédito | La aprobación de nuevas condiciones de crédito se separa del registro del pedido. | R-ATN o R-FAC | R-PRO | Cliente, condición, fundamento, responsable y vigencia | — |
| SOD-05 · Pedido | Los cambios materiales posteriores a la aceptación requieren decisión y nueva evidencia. | R-ATN | R-PRO | Versión anterior y posterior, causa y aceptación | [INT-01](../integraciones/INT-01-CRM-ERP.md), F-02 |
| SOD-06 · Accesos | Quien solicita una elevación de privilegios no la valida. | R-PRO | Otro R-PRO | Solicitud, aprobación y grupos antes y después | — |
| SOD-07 · Cuenta de servicio | La identidad técnica registra operaciones permitidas y no adquiere facultades comerciales. | R-INT | R-PRO y R-TEC | Cuenta, evento, origen, resultado y auditoría | Condicional a una interfaz aprobada |

En una operación iniciada por un propietario, la aprobación sensible corresponde al otro propietario. La revisión no se acredita con una segunda acción del mismo usuario. La evidencia se incorpora al rastro definido en el [plan de trazabilidad y auditoría](../../datos/trazabilidad/plan-trazabilidad-auditoria.md).

## 6. Alta, cambio, baja y revisión de usuarios

| Momento | Procedimiento y responsabilidad |
|---|---|
| Alta | R-PRO autoriza el perfil nominal; R-TEC crea una cuenta individual y documenta el alcance. |
| Modificación | Se revisan accesos previos, perfiles concurrentes y compatibilidad con la segregación. |
| Baja | Se desactiva la cuenta y se reasignan sus operaciones abiertas, conservando su identidad en el historial. |
| Revisión | Se cotejan periódicamente los permisos de Odoo y KeyFacil con las responsabilidades vigentes. |

Los perfiles se traducen a grupos y restricciones por registro según los módulos efectivamente utilizados. Mientras R-TEC no tenga responsable, estas tareas técnicas quedan pendientes de asignación.

## 7. Sistemas externos e incidentes

Las transiciones entre módulos de la misma instancia de Odoo, como el paso de CRM a ERP, no requieren una cuenta de integración. Si se aprueba una interfaz externa, se usará una identidad no humana (R-INT) con alcance mínimo, operaciones identificables y registro de resultados.

Ante un incidente de seguridad se suspende la identidad afectada, se preservan las evidencias, se identifican las operaciones comprometidas, se corrigen con autorización y se restituye el servicio tras la revisión. La conciliación manual documentada con KeyFacil actúa como alternativa de continuidad.

## 8. Verificación

| Punto de control | Reglas | Verificación por prueba |
|---|---|---|
| Cliente y cotización | PR-02, PR-04 | Restricciones de lectura y cambios en contactos y datos fiscales |
| Precio y descuento | PR-02, PR-04 | Aprobación por usuario diferente y conservación de versiones |
| Pedido y crédito | PR-02, PR-04, PR-06 | Aceptación registrada y decisión del propietario para crédito nuevo o modificado |
| Stock | PR-05, PR-04 | Separación entre recepción o entrega y ajuste autorizado |
| KeyFacil y cobro | PR-06, PR-04 | Conciliación de referencia fiscal y pago; anulación independiente |
| Cuenta de servicio | PR-08 | Alcance técnico mínimo, solo si se incorpora una interfaz externa |

Cada caso de prueba enlaza la regla (PR), el control de segregación (SOD) y el registro de trazabilidad, con resultado esperado, resultado obtenido y evidencia identificable.

## 9. Fuentes

* [Contexto de la empresa](../base/contexto-empresa.md)
* [Vistas C4](../vistas/consolidado-diagramas.md)
* [Flujo O2C](../../procesos/o2c/flujo.md) y [flujo de inventario](../../procesos/inventario/flujo.md)
* [Decisiones comerciales](../../procesos/comercial-crm/decisiones-comerciales.md)
* [Plan de trazabilidad y auditoría](../../datos/trazabilidad/plan-trazabilidad-auditoria.md)

## 10. Historial de cambios

| Versión | Fecha | Autor | Cambio |
|---|---|---|---|
| 0.1 | 17/10/2026 | Luis Núñez | Versión inicial del modelo de autorización |
