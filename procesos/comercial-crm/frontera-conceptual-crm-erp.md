# Frontera CRMRP: transición del compromiso comercial a la ejecución ERP

## 1. Metadatos

- **Documento:** Frontera CRM-ERP
- **Versión:** 1.0
- **Fecha:** 16/10/2026
- **Estado:** Propuesta para revisión
- **Autor:** Gabriel Martínez
- **Documento relacionado:** [ADR-004 — Adoptar Odoo Community con fronteras funcionales claras para CRM y ERP](../../arquitectura/decisiones/ADR-004-odoo-community-fronteras-crm-erp.md)

## 2. Propósito

Este documento define, de forma funcional, cómo se pasa del **CRM**, donde se analiza y acuerda una oportunidad comercial, al **ERP**, donde se acepta, prepara y ejecuta el pedido.

La frontera no representa necesariamente una integración técnica inmediata. Representa el punto en el que el compromiso comunicado al cliente deja de ser únicamente comercial y debe convertirse en una operación ejecutable, con condiciones verificables, responsables y trazabilidad.

La regla principal es:

> El CRM conserva el contexto y el compromiso comercial; el ERP recibe las condiciones aceptadas y gestiona la ejecución operativa.

Esta frontera complementa la decisión propuesta en el ADR-004, que establece Odoo Community como plataforma común para CRM, Ventas e Inventario, manteniendo KeyFacil como sistema externo para la emisión de comprobantes hasta que exista una decisión distinta.

## 3. Qué conserva cada lado

| Área | CRM: compromiso comercial | ERP: ejecución operativa |
|---|---|---|
| Identidad | Cliente, contacto, maestro de obra, cuenta relacionada y nivel de identificación disponible | Datos necesarios para crear o utilizar el cliente del pedido y continuar la operación |
| Oferta | Cotización, versión, productos, cantidades, precios, descuentos, vigencia y condición comunicada | Líneas aceptadas del pedido, precios aplicables y cantidades que deben prepararse |
| Promesas | Fecha o condición prometida, responsable, fundamento y estado de confirmación | Disponibilidad, reserva, preparación, entrega parcial o faltante realmente ejecutado |
| Trazabilidad | Relación entre consulta, oportunidad, cotización, comunicación y aceptación | Relación entre pedido, reserva, movimientos, entrega, comprobante y cobro |
| Gobierno | Quién puede aprobar descuentos, precios especiales o promesas al cliente | Quién puede confirmar, reservar, entregar, registrar diferencias y conciliar |

El CRM no debe afirmar que un producto está reservado, entregado o cobrado. El ERP no debe perder la versión de la oferta ni las condiciones que originaron el pedido.

## 4. Condiciones mínimas para aceptar el paso al ERP

El paso de una cotización aceptada hacia un pedido ERP requiere, como mínimo:

1. **Identidad suficiente:** debe conocerse a quién se atribuye la operación y quién es el contacto responsable. La identificación formal completa no es obligatoria para registrar una consulta o preparar una cotización, pero debe validarse antes del pedido cuando sea necesaria para la operación, la entrega o la emisión del comprobante.
2. **Oferta identificable:** debe existir una cotización concreta, con versión, productos, unidades, cantidades, precios y descuentos aplicables.
3. **Promesas diferenciadas:** toda promesa de disponibilidad, fecha o entrega debe indicar si está confirmada, pendiente o condicionada.
4. **Aceptación registrada:** debe conservarse quién aceptó, qué versión aceptó, cuándo lo hizo y bajo qué condiciones.
5. **Responsable autorizado:** las decisiones sensibles deben quedar asociadas a la persona que las aprobó, especialmente descuentos, crédito, disponibilidad crítica y condiciones excepcionales.
6. **Origen reconstruible:** el pedido debe poder relacionarse con la cotización, y la cotización con la oportunidad y la consulta original.
7. **Excepciones visibles:** cualquier diferencia entre lo cotizado y lo pedido debe registrarse como cambio, no corregirse silenciosamente.

## 5. Componentes del CRM en la frontera

Para esta frontera, el CRM se entiende mediante cuatro componentes:

| Componente | Qué representa | Ejemplos en MIGAL |
|---|---|---|
| **Análisis** | Interpretación de la necesidad y madurez de la oportunidad | Necesidad concreta, obra activa, probabilidad, competencia y decisor |
| **Señales** | Indicadores que justifican avanzar o detenerse | Lista de materiales, cantidades aproximadas, solicitud de descuento, consulta de entrega o crédito |
| **Datos** | Información registrada para operar y reconstruir el caso | Cuenta, contacto, canal, productos, cantidades, precios, versiones, responsables y fechas |
| **Resultados** | Estado producido por la interacción comercial | Cotización enviada, ganada total, ganada parcial, perdida, aceptación o excepción pendiente |

Estos componentes no son etapas separadas obligatorias. Son una forma de distinguir entre lo que se interpreta, lo que se observa, lo que se registra y el resultado que se obtiene.

## 6. Trazabilidad y manejo de evidencias

La cadena mínima de referencia será:

```text
Consulta → Lead/Oportunidad → Cotización/Versión → Aceptación → Pedido ERP
```

Cuando la operación continúe, la cadena podrá ampliarse:

```text
Pedido → Reserva/Preparación → Entrega → Referencia KeyFacil → Cobro → Posventa
```

Cada objeto debe conservar su propio identificador y una relación con el identificador anterior. No es necesario almacenar toda la conversación original para cada operación. Debe conservarse una referencia suficiente de la comunicación y evidencia adicional cuando la decisión sea relevante o pueda ser discutida posteriormente.

| Situación | Registro mínimo | Evidencia adicional |
|---|---|---|
| Consulta o seguimiento | Fecha, canal, responsable, necesidad y próxima acción | Referencia al mensaje o nota; captura solo si aporta valor |
| Cotización | Versión, líneas, precios, descuento, vigencia y fuente de precios | Documento enviado o registro de comunicación |
| Descuento o condición especial | Motivo, decisión, aprobador y fecha | Soporte de la autorización, si existe |
| Promesa de disponibilidad o fecha | Producto, cantidad, condición, fecha, responsable y estado | Consulta de stock, mensaje o captura cuando la promesa sea crítica |
| Aceptación del cliente | Versión aceptada, fecha, persona y condiciones | Mensaje, documento, firma o evidencia equivalente |
| Pedido ERP | Referencia a cotización y aceptación, cantidades y condiciones trasladadas | Registro del pedido y resultado de validación |

La evidencia debe ser proporcional. Para una fecha o una interacción simple puede bastar el registro de fecha, responsable y referencia. Para una aprobación de descuento, una promesa crítica o una aceptación controvertible, conviene conservar el soporte disponible. No deben guardarse credenciales ni datos personales innecesarios.

## 7. Accesos y gobierno funcional

- **Atención/Ventas:** registra consultas, oportunidades, cotizaciones, comunicaciones y próximas acciones.
- **Propietarios:** aprueban descuentos, condiciones excepcionales, crédito y promesas que comprometan recursos o margen.
- **Almacén:** consulta el pedido operativo y registra disponibilidad real, preparación, entrega y diferencias. No necesita acceder a todo el detalle comercial o crediticio.
- **Administración:** consulta el pedido y la entrega para gestionar la referencia de KeyFacil, conciliación y cobro según el procedimiento aprobado.
- **Cliente o contacto autorizado:** proporciona la aceptación y las condiciones necesarias para convertir la oferta en pedido.

Una misma persona puede cumplir varias funciones en la operación real, pero el registro debe conservar qué función ejerció en cada decisión. La frontera propuesta no presume que todos estos permisos estén ya configurados en Odoo.

## 8. Información que no debe exigirse prematuramente

No se debe exigir, para toda consulta o cotización:

- DNI o RUC cuando el cliente aún no lo ha proporcionado y la operación no lo requiere;
- datos fiscales completos antes de saber si la cotización será aceptada;
- una reserva de inventario solo por haber enviado una cotización;
- una promesa de entrega sin confirmación del responsable de stock;
- una captura de pantalla para cada interacción;
- duplicar manualmente en el ERP información que ya tenga una referencia clara en el CRM.

La información debe aumentar conforme aumenta el compromiso. Una consulta necesita pocos datos; una cotización necesita una oferta reconstruible; un pedido necesita identidad, aceptación y condiciones operativas suficientes.

## 9. Siguiente decisión a tomar

La siguiente decisión debe definir el **contrato funcional de aceptación CRM → ERP**, es decir:

1. qué campos son obligatorios para convertir una cotización aceptada en pedido;
2. cómo se registra la aceptación del cliente;
3. qué datos se copian y cuáles se referencian desde la cotización;
4. qué roles pueden confirmar el pedido, reservar stock y modificar condiciones;
5. cómo se registran diferencias entre lo cotizado, lo aceptado y lo entregado;
6. qué evidencia mínima se conserva en cada transición;
7. cómo se enlaza posteriormente la referencia de KeyFacil.

Esta decisión debe validarse mediante una prueba en la versión de Odoo que utilice MIGAL. En particular, debe comprobarse la conversión de oportunidad a cotización, la confirmación de la cotización, la generación del pedido y el comportamiento ante stock insuficiente o entrega parcial.

## 10. Relación con el ADR-004

El ADR-004 propone Odoo Community como plataforma común para CRM, Ventas e Inventario, con fronteras funcionales claras. Este documento desarrolla una de esas fronteras: el paso desde el contexto y compromiso comercial hacia la ejecución del pedido.

Por tanto:

- el ADR-004 establece la decisión arquitectónica general;
- este documento define el significado funcional de la frontera CRM → ERP;
- la configuración concreta de Odoo, los permisos y las pruebas quedan pendientes;
- KeyFacil continúa siendo externo y su referencia debe conservarse de forma trazable;
- no se declara que la integración técnica ni los controles estén implementados.

## Fuentes utilizadas

- [ADR-004 — Adoptar Odoo Community con fronteras funcionales claras para CRM y ERP](../../arquitectura/decisiones/ADR-004-odoo-community-fronteras-crm-erp.md)
- [Escenario comercial: flujo marketing → lead → oportunidad → cotización](../../procesos/comercial-crm/escenario-crm.md)
- [Aporte al flujo: lead, oportunidad y cotización](../../procesos/comercial-crm/lead-oportunidad-cotizacion.md)
- [Análisis de la situación actual y mejora propuesta](../../procesos/comercial-crm/analisis-situacion-y-mejora.md)
- [Decisiones comerciales y responsabilidades](../../procesos/comercial-crm/decisiones-comerciales.md)
- [SIPOC — Order to Cash](../../procesos/o2c/sipoc.md)
- [INT-01: CRM y ERP](../../arquitectura/integraciones/INT-01-CRM-ERP.md)
- [Plan de trazabilidad y auditoría](../../datos/trazabilidad/plan-trazabilidad-auditoria.md)
- [Datos transaccionales por etapa](../../datos/transaccionales/README.md)
- [Mapa de procesos de nivel 1](../../procesos/mapa-nivel-1/mapa-procesos.md)
- [Caso normal CRM](../../procesos/comercial-crm/caso-normal.md)
- [Facturación y referencia externa](../../procesos/comercial-crm/facturacion.md)
