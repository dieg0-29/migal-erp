# Registro de identificadores y linaje

## 1. Metadatos

* **Fecha:** 17/10/2026
* **Versión:** 0.1
* **Autores:** Brenda Mirano
* **Custodio:** R-PRO

## 2. Propósito

Registrar en un solo lugar todos los prefijos de identificadores y espacios de códigos del repositorio, para que ningún código se repita con otro significado, y describir cómo se encadena una operación.

## 3. Identificadores de entidad

Cada objeto conserva su propio identificador y el enlace al anterior. Los datos de prueba agregan `-SIM` después del prefijo.

| Prefijo | Entidad | Ejemplo `[SIM]` | Relación |
|---|---|---|---|
| CLI | Cuenta (cliente) | `CLI-SIM-001` | Agrupa contactos y obras |
| CON | Contacto | `CON-SIM-002` | Pertenece a una cuenta |
| DIR | Dirección u obra | `DIR-SIM-001` | Contexto de la cuenta; destino futuro |
| PRD | Producto | `PRD-SIM-001` | Línea de cotización |
| OPP | Oportunidad | `OPP-SIM-001` | Cuenta, contacto y cotizaciones |
| COT-nnn-Vnn | Cotización y versión | `COT-SIM-001-V01` | Una versión no sustituye sin rastro a otra |
| DEC | Decisión comercial | `DEC-SIM-001` | Oferta, línea o condición afectada |
| PED | Pedido | `PED-SIM-001` | Cotización aceptada |
| ENT | Entrega | `ENT-SIM-001` | Pedido y ubicación |
| CPE | Comprobante (referencia de KeyFacil) | `CPE-SIM-001` | Pedido |
| PAG | Pago | `PAG-SIM-001` | Comprobante |
| PROV | Proveedor | `PROV-SIM-001` | Compra y recepción |
| CORR | Correlación entre sistemas | — | Solo si existe una interfaz externa (TR-13) |

Los prefijos son convenciones del proyecto, no secuencias garantizadas en Odoo.

## 4. Espacios de códigos

| Código | Significado | Documento dueño |
|---|---|---|
| RN-nn, CT-nn | Reglas de negocio y sus controles | [Decisiones comerciales](../../procesos/comercial-crm/decisiones-comerciales.md) |
| EXC-nn | Excepciones comerciales | [Decisiones comerciales](../../procesos/comercial-crm/decisiones-comerciales.md) |
| CAM-nn | Campañas | [Cuenta, contacto y canales](../../procesos/comercial-crm/cuenta-contacto-canales.md) |
| ETP-nn | Etapas del flujo comercial | [Escenario CRM](../../procesos/comercial-crm/escenario-crm.md) |
| DQ-nn | Reglas de calidad de datos | [Reglas de calidad](../calidad/reglas-calidad.md) |
| TR-nn | Trazas de auditoría | [Plan de trazabilidad](plan-trazabilidad-auditoria.md) |
| CP-nn | Casos de prueba | [Caso normal](../../procesos/comercial-crm/caso-normal.md) (CP-01), [caso de excepción](../../procesos/comercial-crm/caso-excepcion.md) (CP-02) |
| R-xxx, PR-nn.nn, SOD-nn | Perfiles, permisos y segregación | [Modelo de autorización](../../arquitectura/seguridad/modelo-autorizacion.md) |
| INT-nn, EV-nn, F-nn | Integraciones, sus eventos y fronteras | [Integraciones](../../arquitectura/integraciones/INT-01-CRM-ERP.md); fuera del documento se citan como `INT-01/EV-03` |
| O2C-R/E/C, P2P-R | Reglas, eventos y controles de los macroprocesos | [O2C](../../procesos/o2c/reglas.md), [P2P](../../procesos/p2p/reglas.md) |
| ADR-nnn, VER-nn, CA-nn | Decisiones, versiones y ajustes de arquitectura | [Decisiones](../../arquitectura/decisiones/), [versiones](../../arquitectura/versiones/README.md) |

## 5. Linaje mínimo

| Información | Procedencia | Conservación |
|---|---|---|
| Necesidad | Consulta del cliente o contacto | Resumen fiel vinculado a la interacción |
| Cuenta u obra | Contexto levantado y ficha existente | Buscar, validar y relacionar; no fusionar automáticamente |
| Producto y unidad | Catálogo revisado | Variante correcta; se conserva la línea cotizada |
| Precio ofrecido | Referencia y decisión del propietario | Versión, motivo y autor del cambio |
| Seguimiento | Próximo paso comercial | Acción, fecha y responsable |
| Resultado | Respuesta o hecho posterior | Fuente y motivo; una cotización no prueba una compra |

## 6. Recorrido del caso normal

`CLI-SIM-001` → `CON-SIM-002` / `DIR-SIM-001` → `OPP-SIM-001` → `COT-SIM-001-V01` → líneas `PRD-SIM-001`, `PRD-SIM-002` y `PRD-SIM-003`. Cuando el caso continúe en el ERP, la cadena sigue con `PED-SIM-001` → `ENT-SIM-001` → `CPE-SIM-001` → `PAG-SIM-001`.

## 7. Captura y corrección

Se registra objeto, acción, actor, fecha y hora con zona, valor anterior y posterior cuando corresponda, motivo y evidencia. Antes de corregir se revisan las referencias dependientes. Un enlace roto se registra como incidencia, no se completa con un evento ficticio.

## 8. Historial de cambios

| Versión | Fecha | Autor | Cambio |
|---|---|---|---|
| 0.1 | 17/10/2026 | Brenda Mirano | Versión inicial como registro único de identificadores y códigos |
