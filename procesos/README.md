# Procesos

Esta carpeta contiene el modelado de los **procesos empresariales analizados para Ferre & Inversiones MIGAL**. Su propósito es mostrar cómo fluye el valor de extremo a extremo, qué actores participan, qué decisiones se toman y qué evidencia permite reconstruir cada proceso.

## Estructura hasta el Examen Parcial

```text
procesos/
├── README.md
├── mapa-nivel-1/
├── o2c/
├── p2p/
├── inventario/
└── comercial-crm/
```

### `mapa-nivel-1/`

Presenta la vista general de los procesos de la empresa y permite ubicar los macroprocesos estratégicos, core y de soporte.

### `o2c/`

Documenta **Order to Cash**, desde la necesidad comercial hasta el cobro o el cierre explícito de una excepción.

Puede incluir:

- SIPOC;
- flujo;
- reglas;
- eventos y controles;
- indicadores.

### `p2p/`

Documenta **Procure to Pay**, desde una necesidad de compra autorizada hasta el pago conciliado.

Puede incluir:

- SIPOC;
- flujo;
- reglas;
- eventos y controles;
- indicadores.

### `inventario/`

Contiene artefactos específicos de la gestión de inventario que no deben confundirse automáticamente con P2P.

Aquí se documentan, por ejemplo, movimientos, recepciones, despachos, ajustes y coordinación del stock con otros procesos.

### `comercial-crm/`

Contiene el incremento comercial del proyecto.

Hasta PC2 comprende principalmente:

- cuenta y contacto;
- canales y fuentes;
- lead;
- oportunidad;
- cotización;
- decisiones comerciales;
- frontera conceptual CRM–ERP;
- caso normal y excepción.

Los artefactos de pedido, facturación y posventa se incorporan cuando el curso avance a ese tramo.

## Convenciones

Cada proceso debe declarar, cuando corresponda:

- propósito;
- punto de inicio y fin;
- actores;
- entradas y salidas;
- eventos o estados;
- datos;
- reglas y controles;
- excepciones;
- responsables;
- indicadores;
- fuentes, supuestos y pendientes.

Los documentos deben separar claramente el **AS-IS** de las propuestas **TO-BE** para no presentar una solución futura como si ya existiera en la empresa.
