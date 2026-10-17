# CP-02: Caso de excepción — presión de precio por competencia

## 1. Metadatos

* **Fecha:** 17/10/2026
* **Versión:** 0.1
* **Autores:** Diego Pinedo
* **Proceso:** [Flujo comercial](../../procesos/comercial-crm/flujo-comercial.md), paso 5
* **Estado:** Por ejecutar en Odoo

## 2. Objetivo

Comprobar que una excepción de precio se decide por un propietario, queda en una nueva versión con motivo y autorizador, y que el resultado parcial se registra sin declarar perdida la oportunidad.

`[E]` Es la excepción prioritaria porque afecta el margen de los productos con menos holgura (cemento y fierro) y hoy no deja rastro de qué se concedió ni por qué. `[FN-01][FN-02]`

## 3. Datos de entrada `[SIM]`

| Objeto | Valor del catálogo |
|---|---|
| Cuenta | `CLI-SIM-002` · Julio César Rojas Cárdenas (obra) |
| Contacto decisor | `CON-SIM-003` · Julio César Rojas Cárdenas (dueño de obra) |
| Contacto operativo | `CON-SIM-004` · Víctor Hugo Palomino Chacón (maestro de obra) |
| Canal / fuente / campaña | WhatsApp / no registrada `[ND]` / ninguna |
| Oportunidad | `OPP-SIM-002` · Cemento y fierro para columnas · probabilidad Alta · competencia Sí · responsable R-PRO |
| Decisión | `DEC-SIM-001` · descuento por competencia · ajuste autorizado por el dueño · 16/10/2026 |
| Precio de la competencia | Otra ferretería mejora el precio del fierro; importe no registrado `[ND]` |

| Línea | Producto | Cant. | V01 (referencia) | V02 (ofrecido) | Motivo | Autorizó | Resultado de línea |
|---|---|---:|---:|---:|---|---|---|
| 1 | `PRD-SIM-001` Cemento | 80 | S/ 31.20 | S/ 31.00 | Volumen | Dueño | Adjudicada |
| 2 | `PRD-SIM-002` Fierro | 60 | S/ 40.50 | S/ 40.10 | Competencia | Dueño | No adjudicada |
| | **Suma** | | **S/ 4,926.00** | **S/ 4,886.00** | | | |

Beneficio concedido en V02: S/ 16.00 en cemento y S/ 24.00 en fierro (S/ 40.00 en total). Importe adjudicado a MIGAL: S/ 2,480.00.

## 4. Precondiciones

* Mismo recorrido que [CP-01](CP-01-caso-normal.md) hasta emitir `COT-SIM-002-V01`.
* `[E]` No existe un porcentaje máximo de descuento; cualquiera de los propietarios puede autorizar ajustes.

## 5. Pasos

| Paso | Acción | Actor | Regla | Evidencia esperada |
|---|---|---|---|---|
| 1 | El maestro informa que otra ferretería ofrece un precio menor y pide mejorarlo | R-ATN | EXC-01 | Solicitud registrada con línea afectada |
| 2 | Un propietario evalúa referencia, cantidad, mezcla de productos, relación con el maestro y entrega | R-PRO | EXC-01 | Información considerada |
| 3 | Se autoriza el ajuste y se emite V02 conservando V01 | R-PRO | RN-04, SOD-01 | V02 con referencia, ofrecido, diferencia, motivo y autorizador por línea; `DEC-SIM-001` con fecha |
| 4 | El cliente compra el cemento en MIGAL y el fierro en otra ferretería | R-ATN | — | Resultado "Ganada parcial", motivo *precio de competencia en fierro* |

## 6. Opciones evaluadas

| Opción | Descripción | Evaluación |
|---|---|---|
| A | El propietario autoriza un ajuste y se emite V02 | **Elegida** (`DEC-SIM-001`) |
| B | Mantener V01 y aceptar perder la línea | Válida si el margen no lo permite; la oportunidad sigue abierta mientras el cliente decide |
| C | Quien atiende rebaja el precio sin autorización | Descartada: es el riesgo AS-IS de vender cerca del costo |

## 7. Resultado esperado

| Elemento | Resultado |
|---|---|
| Decisión | Ajustar cemento (volumen) y fierro (competencia) en una nueva versión |
| Responsable | R-PRO (dueño, responsable de la oportunidad) |
| Impacto para el cliente | Respuesta explicable, igual sin importar quién atienda; decide dónde comprar cada línea con información clara |
| Respuesta | Registrar "Ganada parcial", no "Perdida", porque hubo venta efectiva |

`[I]` El ajuste de S/ 0.40 por unidad en fierro no bastó para retener la línea. Registrar el motivo permite a los propietarios revisar con datos en qué productos la competencia gana por precio.

## 8. Resultado obtenido

Pendiente de ejecución. Registrar entorno, usuario, fecha, resultado y evidencia en `pruebas/resultados/`.

## 9. Límites

No prueba pedido, reserva, entrega, comprobante ni cobro.

## 10. Historial de cambios

| Versión | Fecha | Autor | Cambio |
|---|---|---|---|
| 0.1 | 17/10/2026 | Diego Pinedo | Versión inicial; reúne el caso de excepción y su ficha de análisis |
