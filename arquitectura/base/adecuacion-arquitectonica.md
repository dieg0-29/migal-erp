# Adecuación arquitectónica al caso MIGAL

**Estado:** evaluación propuesta; no acredita configuración ni aprobación del negocio.  
**Corte:** base PC1 y ampliación comercial PC2; ejecución posterior separada.

## Necesidad y respuesta propuesta

MIGAL requiere recuperar el contexto comercial disperso en conversaciones, notas y conocimiento de los propietarios. La propuesta combina una plataforma modular con responsabilidades funcionales y datos compartidos. El tamaño del negocio exige que la complejidad operativa se justifique por el valor obtenido.

| Necesidad del caso | Respuesta de diseño | Fundamento | Límite y validación |
|---|---|---|---|
| Reconocer cliente, maestro y obra | Cuenta con contactos y direcciones relacionados | [Contexto CRM](../../procesos/comercial-crm/cuenta-contacto-canales.md) | Validar relaciones y búsqueda; no asumir un único interlocutor |
| Recuperar propuestas y negociaciones | Oportunidad, próxima acción y versiones de cotización | [Flujo comercial](../../procesos/comercial-crm/lead-oportunidad-cotizacion.md) | Verificar cómo conservar versiones en la configuración elegida |
| Compartir productos y precios | Catálogos con identificadores estables y responsable de actualización | [Maestros](../../datos/maestros/productos.md) | No existe todavía catálogo productivo validado |
| Coordinar tienda y dos almacenes | Inventario central con ubicación de cada movimiento | [ADR-004](../decisiones/ADR-004-odoo-community-fronteras-crm-erp.md) | La representación lógica de los puntos físicos sigue pendiente |
| Convivir con emisión externa | KeyFacil conserva emisión; referencia y conciliación posteriores | ADR-004 | No presupone conector ni validez fiscal de documentos internos |
| Operar sin TI dedicado | Mantener pocos componentes, configuración documentada y soporte identificable | [ADR-001](../decisiones/ADR-001-seleccion-erp.md) | Deben definirse administrador, alojamiento, costos y recuperación |
| Reconstruir decisiones sensibles | Permisos funcionales, motivo, autor y evidencia | [D09](../seguridad/d09-autorizacion-y-segregacion.md), [D10](../../datos/trazabilidad/d10-plan-trazabilidad-auditoria.md) | Controles propuestos; verificar viabilidad con dos propietarios |

## Criterios de adecuación

1. **Proporcionalidad:** no agregar una interfaz externa si basta una transición funcional o un procedimiento explícito.
2. **Trazabilidad:** conservar la relación entre necesidad, propuesta, decisión y evidencia sin exigir datos fiscales para toda consulta.
3. **Incrementalidad:** PC2 documenta el tramo previo al pedido; inventario, facturación, cobro y posventa se preparan como extensión.
4. **Operabilidad:** cada configuración debe tener responsable, instrucciones de mantenimiento y alternativa ante indisponibilidad.
5. **Validación:** distinguir capacidad esperada, configuración realizada y resultado comprobado.

## Compromisos y riesgos

Una sola plataforma reduce duplicidades, pero concentra la dependencia de disponibilidad, calidad de maestros y administración. La conciliación manual con KeyFacil evita anticipar un desarrollo, aunque mantiene riesgo de doble digitación. Los módulos adicionales pueden ampliar capacidades, pero requieren revisar licencia, compatibilidad y mantenimiento. Estas consecuencias deben evaluarse antes de aceptar los ADR, actualmente propuestos.

## Comprobaciones para aceptar la adecuación

| Comprobación | Evidencia esperada | Estado |
|---|---|---|
| Contacto relacionado con cuenta y obra | Caso sintético y búsqueda reproducible | Pendiente |
| Cotización y cambio de precio reconstruibles | Versiones, motivo y autorizador | Pendiente |
| Roles compatibles con personas reales | Asignación funcional validada por propietarios | Pendiente |
| Entorno recuperable y administrable | Configuración, copia y prueba de restauración | Futuro; pendiente |
| Referencia fiscal conciliable | Ejemplo de vínculo y procedimiento sin duplicar emisión | Futuro; pendiente |

## Fuentes y pendientes

Se utilizan las afirmaciones registradas en [fuentes de negocio](../../fuentes/fuentes-negocio.md), no una nueva entrevista. Falta localizar sus soportes primarios y validar presupuesto, soporte y despliegue. La evaluación no corrige automáticamente las discrepancias de los diagramas o flujos de PC1; véase [evolución de arquitectura](../versiones/cambios-arquitectura.md).
