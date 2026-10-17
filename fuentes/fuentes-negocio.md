# Registro de fuentes y evidencia del negocio

Este documento registra de dónde provienen las afirmaciones utilizadas para describir a MIGAL y diferencia las **fuentes del negocio** de las **referencias docentes**.

## 1. Fuentes del negocio

| ID | Fuente | Fecha | Uso principal | Observación |
|---|---|---:|---|---|
| `FN-01` | *Monografía 1 - Grupo 1 - SI704V · Ferre & Inversiones MIGAL* | 15/10/2026 | Operación, actores, canales, precios, cotizaciones, reparto, clientes de obra, responsabilidades | Documento elaborado por el equipo a partir de información recolectada |
| `FN-02` | Aclaraciones de campo registradas por Brenda sobre la operación familiar de MIGAL | 16/10/2026 | Contactos, dueño/maestro, seguimiento, competencia, descuentos, cotización, facturación, direcciones e infraestructura actual | Deben conservarse como notas de levantamiento del proyecto |
| `FN-03` | [Contexto de la empresa](../arquitectura/base/contexto-empresa.md) | 25/09/2026 | Contexto inicial, sistemas utilizados y problemática | Revisar consistencia con información más reciente antes de citar como versión definitiva |

## 2. Evidencia relevante extraída

| Afirmación | Fuente |
|---|---|
| MIGAL atiende ventas minoristas y operaciones vinculadas a obras | `FN-01` |
| WhatsApp, llamadas y atención presencial son canales reales | `FN-01`, `FN-02` |
| El maestro de obra puede intermediar entre la ferretería y el responsable de la obra | `FN-01`, `FN-02` |
| El cliente responsable normalmente paga o autoriza; puede delegar compras al maestro | `FN-01`, `FN-02` |
| Precios y condiciones comerciales dependen en gran medida del conocimiento de los propietarios | `FN-01` |
| No existe porcentaje máximo formal de descuento | `FN-01`, `FN-02` |
| Ambos propietarios pueden autorizar descuentos | `FN-01`, `FN-02` |
| La cotización puede quedar en talonario y enviarse por fotografía de WhatsApp | `FN-01` |
| No existe vigencia fija única de cotización | `FN-01`, `FN-02` |
| Antes del pago, un cambio de costos puede provocar una nueva cotización | `FN-01`, `FN-02` |
| La promesa de entrega depende de producto, proveedor, ubicación, carga y recursos | `FN-01`, `FN-02` |
| KeyFacil es utilizado por los propietarios para comprobantes | `FN-01`, `FN-02` |
| La información de clientes/contactos no se encuentra estructurada de forma uniforme | `FN-02` |
| MIGAL no realiza marketing directo sistemático sobre la base de teléfonos | `FN-02` |
| Clientes y maestros comparan precios con otras ferreterías | `FN-02` |
| Una obra puede comprar distintas líneas en distintas ferreterías | `FN-02` |

## 3. Fuentes docentes / de diseño

| ID | Fuente | Uso |
|---|---|---|
| `FC-01` | GE703 · Sesión 6 · CRM, marketing y ventas | Conceptos de cuenta, contacto, interacción, oportunidad, cotización y frontera conceptual CRM–ERP |
| `FC-02` | GE703 · Instrucciones y rúbrica de evaluación v2.1 | Criterios de las entregas del curso |
| `FD-01` | Catálogos GE703 S6 y `Modelo_CRM_ERP_Maestro.xlsx` | Referencia conceptual de objetos y atributos CRM–ERP |

## 4. Regla de uso de los catálogos docentes

Los catálogos del profesor contienen un caso sintético distinto de MIGAL. Por tanto:

- sus estructuras pueden orientar qué conceptos analizar;
- sus valores, clientes, segmentos, porcentajes, políticas, fechas y reglas **no son evidencia de MIGAL**;
- cualquier adaptación al negocio debe justificarse con `FN-01`, `FN-02` u otra evidencia localizada.

Ejemplos de elementos que **no deben copiarse como hechos**:

- descuento máximo del 5 %;
- segmentos industriales del caso docente;
- vigencias de precio del caso docente;
- límites de crédito;
- cargos organizacionales como “jefatura comercial”, si no existen en MIGAL.
