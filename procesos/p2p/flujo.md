# Flujo propuesto — Procure to Pay

**Estado:** diseño funcional para revisión; no describe una implementación de Compras. **Inicio:** necesidad de reposición identificada. **Fin:** recepción y obligación pagada/conciliada, o excepción cerrada con motivo.

## Contexto y alcance

El contexto recibido describe reposición basada en conocimiento de los propietarios y control manual de inventario. El modelo TO-BE propone una referencia común para decisión de compra, recepción y pago. La operación puede comenzar con registro manual controlado; no se presupone RFQ automática al confirmar ventas. PC2 CRM no ejecuta este proceso; su exigencia concreta para EP debe cotejarse con la rúbrica.

## Actores y precondiciones

Propietarios autorizan proveedor, cantidades y condiciones; personal operativo registra mercadería recibida; la función administrativa verifica documentos, pagos y saldos. No son nuevos departamentos. Deben identificarse productos/unidades y proveedor, necesidad y responsable; faltantes se registran antes de comprometer la compra.

## Flujo principal TO-BE

| Paso | Actividad | Salida y control |
|---|---|---|
| 1 | Identificar necesidad por faltante, revisión física o compromiso | Solicitud con producto, unidad, cantidad, motivo y fecha requerida si existe |
| 2 | Consultar referencia de existencias y pendientes | Evitar reponer dos veces la misma necesidad; dato incierto señalado |
| 3 | Consultar proveedor/alternativas y condiciones | Propuesta con precio, unidad, disponibilidad, entrega y pago |
| 4 | Propietario decide y autoriza | Referencia de compra y condiciones aceptadas; no asumir pedido automático |
| 5 | Coordinar recepción y destino físico | Compra, proveedor, punto de recepción y responsable |
| 6 | Contar y revisar mercadería real | Cantidad recibida, diferencias, daños y soporte |
| 7 | Registrar recepción y tratamiento de diferencias | Movimiento/referencia y pendiente; no usar ajuste para ocultar faltante |
| 8 | Cotejar compra, recepción y documento del proveedor | Coincidencia o discrepancia con responsable de resolución |
| 9 | Autorizar y verificar pago según condiciones | Monto, soporte y aplicación; no duplicar pago |
| 10 | Conciliar saldo y cerrar | Pendientes resueltos o excepción explícita |

## Excepciones

| Situación | Respuesta propuesta |
|---|---|
| Stock o necesidad incierta | Confirmar antes de comprometer; registrar información pendiente |
| Proveedor no confirma | Buscar alternativa o renegociar fecha/cantidad; conservar decisión |
| Recepción parcial/dañada | Registrar realidad, saldo y reclamo; no declarar compra completa |
| Precio/documento distinto | Mantener diferencia visible y solicitar revisión antes del cierre |
| Pago anticipado/parcial | Registrar aplicación separada; no confundir pago con recepción |
| Anulación | Motivo, estado previo, autorización y efecto sobre recepción/pago si existen |

## Postcondiciones y evidencia

La historia debe permitir vincular necesidad → decisión → compra → recepción → documento → pago. Si queda saldo físico o económico, el estado es pendiente y no cierre normal. Aceptación requiere caso sintético, responsables, esperado/obtenido y evidencia; todo sigue pendiente de ejecución.

## Relación con otros artefactos

[SIPOC](sipoc.md), [reglas](reglas.md), [eventos/controles](eventos-controles.md), [indicadores](indicadores.md), [proveedores](../../datos/maestros/proveedores.md). El flujo anterior de inventario admite recepción manual y O2C menciona compras automáticas: debe resolverse la discrepancia en la decisión arquitectónica de abastecimiento. Fuentes: [FN-01/FN-02](../../fuentes/fuentes-negocio.md) y [supuestos](../../fuentes/supuestos-y-vacios.md).
