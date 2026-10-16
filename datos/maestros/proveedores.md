# Maestro conceptual de proveedores

**Estado:** preparación para P2P futuro. No hay catálogo de proveedores reales autorizado en esta copia.

## Propósito y campos

Identificar a quién se solicita reposición y relacionar compra, recepción y obligación de pago sin depender de nombres ambiguos o conversaciones aisladas.

| Campo propuesto | Finalidad | Condición |
|---|---|---|
| id_proveedor | Relacionar documentos de abastecimiento | Único y estable |
| nombre_razon_social | Reconocer contraparte | Requerido para compra formal |
| identificacion_fiscal | Comprobar documento cuando proceda | Validar en etapa correspondiente |
| contacto/canal operativo | Consultar disponibilidad y coordinar | Solo datos necesarios |
| productos/categorias | Orientar búsqueda | No garantiza stock del proveedor |
| condiciones_acordadas | Precio, entrega y pago de una operación | Conservar documento y fecha; no inventar plazos |
| estado | Evitar uso de ficha obsoleta | Activo/inactivo propuestos |

## Gobierno y calidad

Propietarios validan relación comercial y condiciones; quien registra recepción consulta la referencia necesaria sin modificar condiciones económicas. Buscar duplicados antes de alta. No utilizar el nombre del proveedor como clave única. Cambios de datos de pago requieren comprobación independiente y registro del cambio; no publicar cuentas ni datos privados en ejemplos académicos.

## Relación con el proceso

Una necesidad de reposición puede compararse entre proveedores. La elección y autorización originan una referencia de compra; recepción documenta cantidades reales y diferencias; Administración coteja documento y pago. Este diseño no presupone módulo Compras ni RFQ automática.

## Pendientes

Validar catálogo autorizado, criterios de selección, disponibilidad, unidades, documentos utilizados y condiciones de pago. Si se necesita un caso académico, usar identificadores PROV-SIM con datos ficticios claramente separados. No hay registros PROV-SIM incorporados al Excel CRM existente.

Referencias: [P2P](../../procesos/p2p/flujo.md), [diccionario](../diccionario/diccionario-datos.md), [privacidad](../privacidad/tratamiento-datos.md), [fuentes](../../fuentes/fuentes-negocio.md).
