# SIPOC — Order to Cash

**Estado:** modelo funcional propuesto; revisión con Procesos pendiente. **Inicio:** necesidad comercial. **Fin:** entrega y cobro conciliados, o excepción cerrada explícitamente.

## SIPOC

| Proveedores de información/recursos | Entradas | Proceso de alto nivel | Salidas | Clientes/receptores |
|---|---|---|---|---|
| Cliente, maestro o referido | Consulta, lista, contacto y contexto de obra | Captar y calificar necesidad | Lead/oportunidad y responsable | Atención y cliente |
| Catálogo y propietarios | Productos, unidades, referencias de precio y condiciones | Preparar y revisar cotización | Versión y decisiones comerciales | Cliente/contacto |
| Cliente responsable/contacto autorizado | Aceptación de versión y condiciones | Comprobar y confirmar pedido | Compromiso operativo trazable | Operación de almacén |
| Inventario y personal operativo | Pedido y disponibilidad por ubicación | Preparar y entregar | Cantidad real, pendiente y evidencia | Cliente y administración |
| Propietario autorizado / KeyFacil | Operación y datos requeridos | Emitir/registrar referencia y conciliar | Comprobante externo vinculado | Cliente y administración |
| Cliente y medios de pago | Soporte y monto recibido | Verificar, aplicar y cerrar | Saldo actualizado y cierre/excepción | Propietarios y apoyo contable pertinente |

“Proveedor” en SIPOC incluye fuente de información; no equivale únicamente a proveedor de mercadería.

## Responsabilidades y límites

Atención conserva contexto y seguimiento; propietarios resuelven condiciones sensibles; almacén documenta operación física; emisión fiscal permanece en KeyFacil según ADR-004. Son funciones que deben mapearse a personas reales. No se presupone RFQ automática ni una factura legal originada en Odoo.

PC2 termina en cotización y seguimiento. Las filas de aceptación/pedido en adelante son extensión futura, no prueba ejecutada. Los casos de venta rápida y obra pueden recorrer distintos pasos; no obligar a crear un lead por cada consulta rápida si no aporta seguimiento.

## Interfaces y controles

Reutilizar cuenta/contacto/producto, identificar versión comunicada, conservar aceptación, separar consulta/reserva/salida y comprobar referencia fiscal/cobro. Los controles se detallan en [reglas](reglas.md) y [eventos](eventos-controles.md).

## Pendientes

Validar crédito, política POS, topología, comprobación de pagos y tratamiento de entregas parciales. El [flujo PC1](flujo.md) aún contiene automatismos contradictorios; este SIPOC no acredita su corrección ni ejecución.

Fuentes: [registro del negocio](../../fuentes/fuentes-negocio.md), [decisiones comerciales](../comercial-crm/decisiones-comerciales.md), [ADR-004](../../arquitectura/decisiones/ADR-004-odoo-community-fronteras-crm-erp.md).
