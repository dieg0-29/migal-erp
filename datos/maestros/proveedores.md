# Proveedores

## 1. Metadatos

* **Fecha:** 17/10/2026
* **Versión:** 0.1
* **Autores:** Brenda Mirano
* **Sistema dueño:** ERP (abastecimiento)
* **Custodio:** R-PRO

## 2. Propósito

Identificar a quién se solicita reposición y relacionar compra, recepción y obligación de pago sin depender de nombres ambiguos o conversaciones aisladas. Prepara el proceso P2P; no presupone el módulo de Compras ni solicitudes de presupuesto automáticas.

## 3. Campos

| Campo | Uso | Obligatorio |
|---|---|---|
| id_proveedor | Relacionar documentos de abastecimiento | Sí |
| nombre_razon_social | Reconocer a la contraparte | Para compra formal |
| identificacion_fiscal | Comprobar documento cuando proceda | Según la etapa |
| contacto y canal operativo | Consultar disponibilidad y coordinar | Solo datos necesarios |
| productos o categorías | Orientar la búsqueda | No garantiza stock del proveedor |
| condiciones_acordadas | Precio, entrega y pago de una operación | Con documento y fecha |
| estado | Evitar fichas obsoletas | Sí |

## 4. Reglas de calidad aplicables

* DQ-01 identificadores únicos y DQ-11 minimización ([reglas de calidad](../calidad/reglas-calidad.md)).
* El nombre del proveedor no se usa como clave única.

## 5. Mantenimiento

| Acción | Perfil | Condición |
|---|---|---|
| Alta y condiciones | R-PRO | Buscar duplicados antes del alta |
| Consulta en recepción | R-ALM | Sin modificar condiciones económicas |
| Cambio de datos de pago | R-PRO | Comprobación independiente y registro del cambio |

## 6. Ejemplo `[SIM]`

No hay proveedores en el catálogo sintético. Si se necesita un caso, se usará el prefijo `PROV-SIM` con datos ficticios.

## 7. Pendientes

* Catálogo autorizado, criterios de selección, unidades, documentos y condiciones de pago.

## 8. Historial de cambios

| Versión | Fecha | Autor | Cambio |
|---|---|---|---|
| 0.1 | 17/10/2026 | Brenda Mirano | Versión inicial con la plantilla de entidad |

Referencias: [flujo P2P](../../procesos/p2p/flujo.md), [fuentes](../../fuentes/fuentes-negocio.md).
