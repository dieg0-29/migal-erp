# Matriz de autorización y segregación de funciones

> Documento convertido desde el adjunto oficial más reciente recibido para PC2; su contenido puede estar sujeto a cambios.


Ferre & Inversiones MIGAL  |  Escenario comercial CRM y ERP

| Responsable asignado | Estado | Documento asociado |
| --- | --- | --- |
| Luis Rodrigo Núñez Príncipe | Modelo de autorización para PC2 | [d09-matriz-permisos.xlsx](d09-matriz-permisos.xlsx) |

Se establece un modelo de autorización orientado a preservar la integridad de las cotizaciones, pedidos, existencias, comprobantes y registros de negocio. Las responsabilidades se distribuyen en perfiles funcionales, sin suponer nuevos puestos de trabajo. MIGAL cuenta con dos propietarios y dos trabajadores; por ello, una misma persona puede realizar varias funciones, sujetas a controles sobre operaciones incompatibles.

El diseño se sustenta en los antecedentes documentales de la PC1 y se desarrolla mediante la matriz anexa [d09-matriz-permisos.xlsx](d09-matriz-permisos.xlsx). Las autorizaciones constituyen reglas de diseño para el escenario CRM–ERP y su cumplimiento se acreditará mediante pruebas por perfil.

## Propósito, alcance y fundamento arquitectónico

La autorización comprende lead, cliente, cotización, pedido, comprobante, precio, stock, crédito, posventa, usuarios y trazas. Se propuso Odoo 18 Community para ventas e inventario, mientras que KeyFacil conserva la emisión fiscal y WhatsApp funciona como canal de comunicación. La tabla relaciona estos antecedentes con el diseño de permisos de D09.

| Ámbito | Antecedentes | Aplicación en D09 |
| --- | --- | --- |
| Equipo | Dos propietarios y dos trabajadores; PC1-02. | Separación por funciones, no por nuevas plazas. |
| Plataforma | Odoo 18 Community como ERP propuesto; PC1-02 y PC1-03. | Control de accesos a ventas, inventario y datos. |
| Facturación | KeyFacil es una plataforma externa; PC1-01 y PC1-05. | Acceso fiscal exclusivo al propietario autorizado. |
| Procesos | Flujos de ventas e inventario; PC1-09 y PC1-10. | Permisos para cotización, pedido, recepción y entrega. |
| Modelo C4 | Vistas C4 de contexto y componentes; PC1-05 a PC1-08. | Delimitación de accesos internos y externos. |

## Roles funcionales y distribución de responsabilidades

Se distinguen seis perfiles funcionales. La asignación de cada perfil corresponde a la función desempeñada y debe conservar la identidad individual de sus usuarios. La segregación se evalúa por operación, aun cuando una misma persona reúna varias responsabilidades.

| Perfil y responsabilidad | Acceso principal y límite |
| --- | --- |
| R-ATN · Atención comercial | Registrar oportunidades, clientes, cotizaciones y aceptación documentada. No aprueba sus descuentos ni emite o anula comprobantes. |
| R-PRO · Propietario aprobador | Decidir excepciones comerciales, condiciones de crédito y regularizaciones sensibles. No autoaprueba excepciones que inició; requiere revisión cruzada. |
| R-ALM · Operación de almacén | Registrar recepción, preparación, despacho y diferencias físicas. No aprueba su propio ajuste de inventario ni administra precios. |
| R-FAC · Facturación y cobro | Registrar número fiscal, cobros y conciliación con KeyFacil. Uso de KeyFacil únicamente por propietario autorizado; anulación con control independiente. |
| R-TEC · Administración técnica | Administrar usuarios, módulos, grupos y continuidad técnica. No posee facultades comerciales por defecto. |
| R-INT · Servicio de interfaz | Intercambiar datos mínimos con sistema externo, únicamente cuando exista integración aprobada. Sin acceso interactivo, aprobación, precios ni anulaciones. |

La correspondencia con la matriz es la siguiente: PR-01 y PR-02 para captación y ejecución comercial; PR-03 y PR-04 para datos maestros y aprobaciones; PR-05 para almacén; PR-06 para facturación y cobro; PR-07 para administración técnica; y PR-08 para una eventual integración externa. Los códigos PR-xx.nn identifican las 60 reglas individuales.

## Reglas de autorización por objeto

La hoja Matriz asigna, para cada combinación de perfil y objeto, las acciones Ver, Crear, Editar, Aprobar y Anular. «Sí» concede el acceso diseñado; «Cond.» lo condiciona a una regla escrita; «No» lo deniega y «N/A» identifica una acción no pertinente. El alcance de lectura aplica el principio de mínimo privilegio.

- Cliente y oportunidad: atención comercial conserva información de contacto y el historial necesario para preparar una oferta. Los datos fiscales y crediticios se utilizan cuando la operación los requiera; no se exigen para captar todo lead.

- Cotización y precio: la oferta conserva precio de referencia, precio presentado, versión, actor y motivo de los cambios. Cualquier excepción negociada por personal comercial requiere aprobación de un propietario diferente del iniciador.

- Pedido e inventario: la aceptación origina el registro comercial; almacén prepara, entrega y deja constancia de cantidades físicas. Los ajustes por diferencias y los cambios materiales posteriores a la aceptación requieren autorización y traza independiente.

- Comprobante y cobro: KeyFacil permanece separado del registro operativo en Odoo. El perfil autorizado consigna referencia fiscal, pago y conciliación, diferenciando emisión, anulación y comprobación de saldos.

## Segregación de funciones y aprobación de excepciones

| Control | Segregación establecida | Evidencia mínima |
| --- | --- | --- |
| SOD-01 · Precio | Preparador y aprobador distintos para una excepción comercial. | Cotización, valores previo/aprobado, motivo, usuario y fecha. |
| SOD-02 · Comprobante | Emisión y autorización de anulación con revisión por propietario distinto. | Comprobante original, motivo, decisión y nota o reversión aplicable. |
| SOD-03 · Inventario | El operador reporta; el propietario autoriza; regulariza quien no ejecutó el conteo original. | Conteo, diferencia, movimiento y autorización. |
| SOD-04 · Crédito | La aprobación de nuevas condiciones de crédito se separa del registro del pedido. | Cliente, condición, fundamento, responsable y vigencia. |
| SOD-05 · Pedido | Modificación posterior a aceptación sometida a decisión y nueva evidencia. | Versión anterior y posterior, causa y aceptación. |
| SOD-06 · Accesos | Quien solicita elevación de privilegios no la valida sin revisión independiente. | Solicitud, aprobación y comparación de grupos. |
| SOD-07 · Servicio externo | La identidad técnica registra operaciones permitidas y no adquiere facultades comerciales. | Cuenta, evento, origen, resultado y auditoría de cambios. |

Se emplean siete controles SOD para separar preparación y decisión de una excepción, emisión y anulación fiscal, movimiento y ajuste de existencias, registro y aprobación de crédito, modificación del pedido, ampliación de accesos y operación de cuentas técnicas. El soporte documental se incorpora al rastro definido en D10.

En una operación iniciada por un propietario, la aprobación sensible corresponde al otro propietario. La revisión no debe acreditarse con una segunda acción del mismo usuario. La aplicación efectiva del control se contrasta en las pruebas de aceptación CP-01 y CP-02.

## Alta, cambio, baja y revisión de usuarios

| Momento | Procedimiento y responsabilidad |
| --- | --- |
| Alta | El propietario autoriza el perfil nominal; administración técnica crea una cuenta individual y documenta el alcance. |
| Modificación | Se revisan accesos previos, funciones concurrentes y compatibilidad con el control de segregación. |
| Baja | Se desactiva la cuenta y se reasignan sus operaciones abiertas, conservando su identidad en la historia. |
| Revisión | Se cotejan periódicamente los permisos de Odoo y KeyFacil con las responsabilidades vigentes. |

Los perfiles funcionales se traducen a grupos y restricciones por registro según los módulos efectivamente utilizados. La administración técnica gestiona las cuentas, mientras que los propietarios autorizan las capacidades de negocio. Se mantienen usuarios nominales y se documentan las modificaciones de permisos.

## Cuenta de servicio e integración con sistemas externos

Las vistas C4 ubican ventas e inventario en el entorno Odoo y describen a KeyFacil como plataforma fiscal externa. Las transiciones entre módulos de una misma instancia no requieren una cuenta de integración adicional. Cuando exista una interfaz externa aprobada, se utilizará una identidad no humana con alcance mínimo, operaciones identificables y registro de resultados.

Ante una incidencia de seguridad, el procedimiento previsto consiste en suspender la identidad afectada, preservar evidencias, identificar las operaciones comprometidas, corregirlas con autorización y restituir el servicio tras la revisión correspondiente. La conciliación manual documentada actúa como alternativa de continuidad.

## Articulación con controles y pruebas de PC2

| Punto de control y permiso | Verificación por prueba |
| --- | --- |
| Cliente y cotización \| PR-01, PR-02, PR-03 | Validar restricciones de lectura y cambios en contactos y datos fiscales. |
| Precio y descuento \| PR-02, PR-04 | Comprobar aprobación por usuario diferente y conservación de versiones. |
| Pedido y crédito \| PR-02, PR-04, PR-06 | Verificar aceptación y decisión propietaria para crédito nuevo o modificado. |
| Stock \| PR-05, PR-04 | Distinguir ejecución de recepción/entrega y ajuste autorizado. |
| KeyFacil y cobro \| PR-06, PR-04 | Conciliar referencia fiscal y pago; revisar la anulación independiente. |
| Interfaz externa \| PR-08, si corresponde | Probar alcance técnico mínimo si se incorpora una interfaz externa. |

La validación contempla comprobar la separación del iniciador y aprobador de descuentos, el trámite autorizado de anulaciones, el ajuste físico con revisión, la restricción de información crediticia y los límites de una cuenta técnica. Cada caso enlaza PR, SOD, CT y TR, con resultado esperado, resultado obtenido y evidencia identificable.

## Referencias documentales de la PC1

| PC1 | Documento del repositorio y utilidad |
| --- | --- |
| 01, 03 | Contexto empresarial y ADR-002: operación actual y Odoo 18 Community. |
| 05, 06 | Diagramas C4 de contexto y contenedores: sistemas y fronteras. |
| 07, 08 | C4 de componentes: responsables y operaciones de ventas e inventario. |
| 09, 10 | Flujos de ventas e inventario: documentos y movimientos de negocio. |
| 12 | Backlog: actividades de implementación y validación del ERP. |

Los códigos PC1-xx se relacionan con los archivos del repositorio migal-erp en la hoja Referencias_PC1 de la matriz D09. Versión documental consultada: commit d14d4e0000ff605af61618262c8777fb9158b188 (16/10/2026). Estas referencias sustentan el diseño, sin sustituir la evidencia de ejecución de los casos de prueba.
