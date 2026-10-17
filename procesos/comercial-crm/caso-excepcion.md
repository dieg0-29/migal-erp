# Caso de análisis — Excepción prioritaria: presión de precio por competencia

**Tipo:** escenario sintético basado en una situación comercial realista de MIGAL  
**Alcance:** CRM previo al pedido  
**Objetivo:** demostrar una decisión comercial excepcional sin inventar una política porcentual

## 1. Contexto

`[E][AS-IS]` Los clientes y maestros de obra pueden comparar precios entre varias ferreterías y comunicar que otro establecimiento ofrece un valor menor. MIGAL procura mantener precios competitivos sin reducirlos de forma que la operación deje de ser conveniente. `[FN-02]`

`[E][AS-IS]` No existe un porcentaje máximo formalizado de descuento; la dueña o el dueño pueden autorizar un ajuste según cantidad, cliente, producto, costo y condiciones de la operación. `[FN-01][FN-02]`

## 2. Datos del escenario

Todos los nombres, cantidades y valores de este caso son **simulados**.

| Elemento | Valor simulado |
|---|---|
| Cuenta | `CLI-SIM-002 · Julio César Rojas Cárdenas` |
| Contacto operativo | `CON-SIM-004 · Víctor Hugo Palomino Chacón` (maestro de obra) |
| Oportunidad | `OPP-SIM-002 · Cemento y fierro para columnas` |
| Producto afectado | `PRD-SIM-002 · Barra corrugada de acero 1/2 pulg x 9 m` |
| Cantidad | 60 unidades |
| Precio de referencia MIGAL | S/ 40.50 por unidad `[SIM]` |
| Referencia comunicada de competencia | Otra ferretería mejora el precio; importe no registrado `[ND]` |
| Solicitud | Mejorar el precio para mantener esa línea en MIGAL |

Los importes no representan precios reales de MIGAL.

## 3. Decisión

**Pregunta:** ¿MIGAL modifica el precio de esta línea?

**Responsable principal:** dueña o dueño.

**Información considerada:**

- costo/referencia disponible;
- cantidad solicitada;
- mezcla de productos de la cotización;
- relación comercial;
- costo o condición de entrega;
- referencia de competencia;
- conveniencia de mantener la venta sin comprometer el margen.

## 4. Respuesta propuesta

### Variante A — Ajuste autorizado

El dueño autoriza un precio de S/ 40.10 `[SIM]` (decisión `DEC-SIM-001`, 16/10/2026).

Se genera una nueva versión:

```text
COT-SIM-002-V01 → precio original
COT-SIM-002-V02 → precio revisado y autorizado
```

Evidencia esperada:

- versión de cotización;
- precio de referencia;
- precio concedido;
- motivo: `competencia`;
- persona que autorizó;
- fecha de la decisión;
- próxima acción con el cliente.

### Variante B — Ajuste no autorizado

Se mantiene el precio vigente y se comunica al cliente que no es posible mejorar la condición.

La oportunidad permanece abierta mientras el cliente decide o se registra posteriormente el resultado.

## 5. Impacto para el cliente

- recibe una respuesta explicable y no arbitraria;
- conoce la condición final ofrecida;
- evita recibir precios diferentes sin trazabilidad según quién atienda;
- puede decidir si compra esa línea en MIGAL o en otra ferretería.

## 6. Resultado posible

Si el cliente compra otros productos en MIGAL pero el fierro en otra ferretería:

> **Resultado comercial:** Ganada parcial  
> **Motivo de no adjudicación de la línea:** Precio de competencia.

No se clasifica toda la oportunidad como perdida si existió una venta efectiva.

## 7. Evidencia de realidad, interpretación y propuesta

| Afirmación | Clasificación |
|---|---|
| Clientes comparan precios con otras ferreterías | `[E][AS-IS]` |
| No existe porcentaje máximo formal de descuento | `[E][AS-IS]` |
| Ambos propietarios pueden autorizar ajustes | `[E][AS-IS]` |
| Registrar motivo y autorizador | `[TO-BE]` |
| Usar versionado de cotización | `[TO-BE]` |
| Precios del caso | `[SIM]` |
| Ganada parcial como resultado separado | `[I][TO-BE]` |

## 8. Fuera de alcance

Este caso no prueba reserva de inventario, pedido ERP, facturación, entrega ni pago.
