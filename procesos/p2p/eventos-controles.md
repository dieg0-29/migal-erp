# Eventos y controles — P2P

**Estado:** hitos funcionales propuestos; sin interfaz ni automatización acreditada.

| Evento | Control propuesto | Responsable funcional | Evidencia |
|---|---|---|---|
| P2P-E-01 Necesidad registrada | P2P-C-01: producto/unidad/cantidad y causa identificables | Solicitante/propietario | Solicitud y fecha |
| P2P-E-02 Compra decidida | P2P-C-02: oferta y autorización coherentes | Propietario | Proveedor, condiciones y decisión |
| P2P-E-03 Recepción contada | P2P-C-03: cotejar real frente a esperado | Operación | Documento, cantidad, ubicación y diferencias |
| P2P-E-04 Diferencia resuelta | P2P-C-04: conservar decisión sin borrar conteo | Propietario/operación | Pendiente, reclamo, devolución o regularización |
| P2P-E-05 Obligación revisada | P2P-C-05: cotejar compra–recepción–documento | Función administrativa | Importes, referencias y discrepancia |
| P2P-E-06 Pago aplicado | P2P-C-06: soporte y no duplicación | Propietario | Monto, medio, fecha y aplicación |
| P2P-E-07 Cierre revisado | P2P-C-07: saldos físicos/económicos explicados | Propietario | Conciliación y motivo de cierre |

## Excepciones y evidencia

Una recepción parcial genera pendiente de cantidad, no ajuste para hacerla coincidir. Un documento discrepante genera revisión; un pago anticipado mantiene pendiente físico. Un cambio de condiciones conserva referencia anterior, motivo y decisión. Capturar identidad individual y momento sin almacenar secretos ni datos privados innecesarios.

## Pruebas propuestas

- Caso normal: necesidad autorizada, recepción completa, documento coincidente, pago y conciliación.
- Parcial: recepción menor a la compra; conservar saldo y no marcar cierre completo.
- Discrepancia: importe distinto; documentar decisión antes de regularización/cierre.
- Duplicidad: mismo soporte de pago presentado dos veces; revisar aplicación existente.

Resultado obtenido y evidencia: pendientes. Los casos nuevos se numeran a partir de CP-03 en `pruebas/casos/`. Las pruebas técnicas de configuración se definen después de elegir mecanismo de registro.

Referencias: [reglas](../catalogo-reglas.md), [flujo](flujo.md), [identificadores](../../datos/trazabilidad/identificadores-y-linaje.md), [fuentes](../../fuentes/fuentes-negocio.md).
