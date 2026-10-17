# Pruebas

Esta carpeta reúne los artefactos que permiten **validar que los procesos, decisiones e integraciones propuestas se comportan como se espera**.

El objetivo no es acumular capturas, sino conservar evidencia suficiente para que otra persona pueda entender qué se probó, con qué datos, cuál era el resultado esperado y qué ocurrió.

## Estructura

```text
pruebas/
├── README.md
├── casos/                 # CP-nn y plantilla-caso.md
└── criterios-aceptacion/
```

Las carpetas `resultados/`, `evidencias/` e `incidencias/` se crean cuando se ejecute el primer caso en Odoo.

### `casos/`

Describe escenarios de prueba con la [plantilla de caso](casos/plantilla-caso.md): [CP-01](casos/CP-01-caso-normal.md) (caso normal) y [CP-02](casos/CP-02-caso-excepcion.md) (excepción de precio).

Cada caso debería incluir, cuando corresponda:

- identificador;
- objetivo;
- precondiciones;
- datos de entrada;
- pasos;
- resultado esperado;
- responsable;
- relación con procesos o decisiones.

### `resultados/`

Registra los resultados obtenidos al ejecutar los casos.

### `evidencias/`

Conserva capturas, exportaciones u otros artefactos que permitan verificar un resultado.

Las evidencias deben usar nombres claros y evitar información sensible.

### `incidencias/`

Registra diferencias entre el comportamiento esperado y el observado, así como su estado o resolución.

### `criterios-aceptacion/`

Define las condiciones mínimas que deben cumplirse para considerar válida una capacidad, escenario o incremento.

## Reglas

- Utilizar datos sintéticos, anonimizados o autorizados.
- Mantener relación entre caso, resultado y evidencia.
- No modificar una evidencia para que parezca un resultado distinto.
- Cuando un hallazgo cambie una decisión o proceso, actualizar también el artefacto correspondiente.
