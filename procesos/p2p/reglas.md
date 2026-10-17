# Reglas funcionales — P2P

**Estado:** propuestas de diseño; validación con propietarios pendiente. Namespace `P2P-R-*` independiente de las reglas RN del [catálogo de decisiones comerciales](../comercial-crm/decisiones-comerciales.md).

| ID | Regla | Responsable funcional | Evidencia y tratamiento |
|---|---|---|---|
| P2P-R-01 | Toda reposición tiene necesidad identificable | Quien solicita / propietario | Producto, unidad, cantidad y causa |
| P2P-R-02 | Revisar existencias y compras pendientes antes de repetir compra | Propietario / operación | Referencias consultadas o incertidumbre |
| P2P-R-03 | Confirmar proveedor, precio y condiciones antes del compromiso | Propietario | Oferta y decisión; cambios requieren nueva constancia |
| P2P-R-04 | Registrar cantidad real recibida, no copiar cantidad comprada sin contar | Operación | Conteo, daños y ubicación |
| P2P-R-05 | Diferencias mantienen saldo físico o excepción | Operación / propietario | Cantidad pendiente y resolución |
| P2P-R-06 | Separar recepción de ajuste de inventario | Operación / propietario | Documento de entrada; ajuste con causa/autorización |
| P2P-R-07 | Cotejar compra, recepción y documento antes de cerrar obligación | Función administrativa / propietario | Coincidencias y discrepancias |
| P2P-R-08 | Verificar pago y aplicación sin duplicidades | Propietario | Soporte, monto, obligación y saldo |
| P2P-R-09 | Mantener trazabilidad de anulaciones/devoluciones | Propietario / operación | Motivo, decisión y efecto físico/económico |
| P2P-R-10 | Cerrar con saldo resuelto o excepción documentada | Propietario | Estado físico y económico separados |

## Límites y excepciones

No se presupone autorización automatizada, regla de reabastecimiento, MTO, valoración contable ni bloqueo de pago. La aprobación sensible se revisará contra el [modelo de autorización](../../arquitectura/seguridad/modelo-autorizacion.md) sin inventar nuevos puestos. Ante un anticipo autorizado, documentar la excepción al orden normal recepción–pago; anticipo no acredita recepción.

El maestro de proveedores no incluye datos reales en esta copia. Las condiciones y plazos son por operación y requieren fuente; no copiar porcentajes o políticas docentes como hechos.

## Validación

Preparar un caso normal y una recepción parcial con documento discrepante; anotar esperado/obtenido y soporte. Estado: no ejecutados. Referencias: [flujo](flujo.md), [proveedores](../../datos/maestros/proveedores.md), [modelo de autorización](../../arquitectura/seguridad/modelo-autorizacion.md), [fuentes](../../fuentes/fuentes-negocio.md).
