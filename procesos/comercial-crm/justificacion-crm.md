# Justificación del CRM

## 1. Metadatos

* **Fecha:** 17/10/2026
* **Versión:** 0.1
* **Autores:** César Joaquín
* **Sistema:** CRM

## 2. Situación actual (AS-IS)

- `[E]` MIGAL es una ferretería con una tienda, dos almacenes, dos propietarios y dos trabajadores. Atiende a clientes frecuentes y a maestros de obra ([contexto de la empresa](../../arquitectura/base/contexto-empresa.md)).
- `[E]` Las consultas llegan por mostrador, WhatsApp y llamadas a los propietarios, sin un horario definido para los mensajes.
- `[E]` Los precios, las compras de cada cliente y otros datos importantes dependen de la memoria de los propietarios. El registro se apoya en notas físicas y en KeyFacil, que se usa de forma incompleta.
- `[E]` No existe un historial único de interacciones y cotizaciones.
- `[ND]` No hay datos medidos sobre cuántas consultas llegan, cuánto se tarda en responder, cuántas cotizaciones terminan en venta ni por qué se pierden las demás.

Con esto se puede describir cómo se atiende, pero no cuánto se pierde. Por eso no se atribuye a MIGAL una tasa de pérdida ni un impacto económico.

## 3. Problema

`[S]` El problema más probable es la falta de un registro compartido de la atención comercial. Si la consulta, lo que pidió el cliente, la cotización enviada y el siguiente paso quedan repartidos entre chats, llamadas y la memoria de cada propietario, retomar un caso o saber en qué terminó depende de una sola persona.

Es una hipótesis de trabajo. Para confirmarla hace falta observar la atención, revisar una muestra autorizada de consultas y conversar con quienes las atienden.

## 4. Propuesta

El CRM en Odoo ordena la atención según el [flujo comercial](flujo-comercial.md), con las reglas del [catálogo](../catalogo-reglas.md) y la transición al ERP definida en [INT-01](../../arquitectura/integraciones/INT-01-CRM-ERP.md). Los riesgos están en INT-01 §7 y los indicadores en [O2C](../o2c/indicadores.md).

## 5. Costos y esfuerzo

No hay una estimación validada, por lo que no se presentan importes. Estos son los rubros que habría que evaluar antes de decidir.

| Rubro | Qué considerar | Estado |
|---|---|---|
| Licencia | `[E]` Odoo 18 Community ([ADR-002](../../arquitectura/decisiones/ADR-002-version-y-edicion.md)) | Community no implica costo cero: faltan hosting, configuración, soporte y mantenimiento |
| Configuración del CRM | Etapas, campos, vistas, permisos y reportes que realmente se necesiten | `[S]` Estimar cuando se validen los requisitos; configurar antes de acordar las reglas automatizaría un proceso sin validar |
| Depuración de datos | Revisar cuentas, contactos y duplicados | `[ND]` No se conoce el volumen ni la calidad actual |
| Capacitación | Tiempo para enseñar a registrar consultas, cotizaciones y próximas acciones | `[ND]` Horas por confirmar |
| Operación | Alojamiento, copias de seguridad, actualizaciones y accesos | `[ND]` MIGAL no tiene personal de TI (R-TEC sin responsable en el [modelo de autorización](../../arquitectura/seguridad/modelo-autorizacion.md)) |
| Relación con facturación | Cómo se vincula la cotización aceptada con el comprobante en KeyFacil | `[E]` KeyFacil se mantiene como emisor externo ([ADR-004](../../arquitectura/decisiones/ADR-004-odoo-community-fronteras-crm-erp.md)) |

Si no se adopta el CRM, la atención seguiría dependiendo de la memoria y de los chats de los propietarios, con un costo de tiempo y de ventas sin seguimiento que hoy no está medido.

## 6. Conclusión

El CRM se justifica donde el problema es de registro: consultas que se pierden entre chats, cotizaciones que nadie puede reconstruir y excepciones de precio que no dejan rastro. No resuelve por sí solo la falta de una lista de precios confiable ni el control del stock, que corresponden al ERP.

El beneficio todavía no está demostrado. Para confirmarlo hay que levantar una línea base, validar con MIGAL las decisiones pendientes y ejecutar los casos de prueba [CP-01](../../pruebas/casos/CP-01-caso-normal.md) y [CP-02](../../pruebas/casos/CP-02-caso-excepcion.md).

## 7. Historial de cambios

| Versión | Fecha | Autor | Cambio |
|---|---|---|---|
| 0.1 | 17/10/2026 | César Joaquín | Versión inicial; conserva del análisis de situación solo lo que no está en otros documentos |

Fuentes: [fuentes del negocio](../../fuentes/fuentes-negocio.md) (FN-01, FN-02).
