# Supuestos, vacíos, propuestas y límites — PC2 MIGAL

## 1. Clasificación

- `[E]` **Evidencia:** respaldada por una fuente o levantamiento.
- `[I]` **Interpretación:** conclusión razonada a partir de la evidencia.
- `[S]` **Supuesto:** condición provisional aún no validada.
- `[ND]` **No determinado:** no existe información suficiente para afirmar el punto.
- `[TO-BE]` **Propuesta:** mejora diseñada por el equipo; no describe la operación actual.
- `[SIM]` **Simulado:** dato ficticio utilizado para un caso académico.

## 2. Realidad confirmada relevante

| Tema | Estado |
|---|---|
| Canales: presencial, WhatsApp y llamadas | `[E][AS-IS]` |
| Referidos y maestros participan en la captación de clientes | `[E][AS-IS]` |
| No existe ficha central estandarizada de cliente/obra/contactos | `[E][AS-IS]` |
| No existe porcentaje máximo formal de descuento | `[E][AS-IS]` |
| Ambos propietarios pueden autorizar descuentos | `[E][AS-IS]` |
| No existe vigencia fija única de cotización | `[E][AS-IS]` |
| Antes del pago puede actualizarse el precio si cambian los costos | `[E][AS-IS]` |
| Una vez pagado se respeta el precio acordado | `[E][AS-IS]` |
| Clientes pueden dividir una compra entre varias ferreterías | `[E][AS-IS]` |
| KeyFacil es operado por los propietarios | `[E][AS-IS]` |

## 3. Propuestas del equipo

| Propuesta | Estado | Justificación |
|---|---|---|
| Ficha CRM central de cuenta/contactos/obra | `[TO-BE]` | Reducir dependencia de memoria y nombres ambiguos |
| Separar dueño de obra y maestro como contactos/roles relacionados | `[TO-BE]` | Refleja relaciones reales de compras para obra |
| Próxima acción + fecha + responsable | `[TO-BE]` | Evitar seguimiento pasivo |
| Probabilidad Baja / Media / Alta | `[I][TO-BE]` | No hay base histórica para porcentajes calibrados |
| Registrar competencia cuando sea relevante | `[TO-BE]` | Clientes comparan precios |
| Versionar cotizaciones | `[TO-BE]` | Conservar cambios por precio o negociación |
| Registrar precio de referencia, precio concedido, motivo y autorizador | `[TO-BE]` | Hacer visible la decisión de descuento |
| Resultado Ganada total / Ganada parcial / Perdida | `[I][TO-BE]` | Una obra puede repartir su compra entre ferreterías |
| Separar uso operativo y promocional del contacto | `[TO-BE]` | Evitar asumir permiso de marketing por tener el teléfono |

## 4. Supuestos y vacíos abiertos

| Tema | Estado | Tratamiento |
|---|---|---|
| Política formal de consentimiento promocional | `[ND]` | Validar antes de campañas directas |
| Tiempo de conservación de datos de cliente | `[ND]` | Definir en una implementación posterior |
| Política de acceso a una futura ficha CRM | `[ND]` | Definir con responsables reales |
| Umbral de descuento resoluble por trabajadores | `[ND]` | No inventar porcentaje |
| Criterio cuantitativo de probabilidad de compra | `[ND]` | Usar escala cualitativa propuesta |
| Criterio formal para otorgar crédito | `[ND]` en PC2 | Fuera del núcleo del incremento actual |
| Tarifa/cobertura fija de reparto | `[E]` No existe formalmente | Tratar caso a caso |
| Regla única de cálculo de precio | `[E]` No existe | No diseñar fórmula universal |

## 5. Correcciones a supuestos de documentos previos

Los siguientes elementos aparecieron en avances anteriores, pero **no deben mantenerse como hechos** sin una nueva decisión explícita:

- `descuento máximo 5 %`;
- `vigencia obligatoria de cotización de 3 días`;
- `RUC/DNI obligatorio para poder cotizar`;
- cargos ficticios como “jefatura comercial” usados para representar a MIGAL;
- bloqueos automáticos o validaciones técnicas no confirmadas;
- considerar una cotización no aceptada como pedido;
- tratar una compra parcial como oportunidad totalmente perdida.

## 6. Fuera de alcance de PC2 v2.1

No se desarrolla en este incremento:

- contrato técnico CRM–ERP;
- payloads, APIs o eventos de integración;
- creación y ejecución del pedido;
- reserva de inventario;
- facturación ejecutada;
- entrega;
- pagos/cobranza;
- posventa;
- agente comercial.

Los catálogos docentes de Pedido, Inventario, Entrega, Factura y Pago se conservan únicamente como contexto para comprender la frontera futura.

## 7. Infraestructura actualizada

`[E][AS-IS]` Para el contexto operativo actual se toma como referencia:

- 1 tienda principal;
- 2 almacenes;
- 2 camiones propios;
- 1 montacargas;
- 1 vehículo eléctrico para entregas pequeñas.

Esta versión reemplaza referencias anteriores inconsistentes sobre la flota.
