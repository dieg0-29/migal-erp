# Arquitectura

Esta carpeta concentra las decisiones y representaciones que explican **cómo se estructura la solución integrada propuesta para Ferre & Inversiones MIGAL** y por qué se ha elegido cada alternativa.

## Contenido

```text
arquitectura/
├── README.md
├── base/
├── decisiones/
├── vistas/
├── integraciones/
└── versiones/
```

### `base/`

Reúne la información que sustenta las decisiones de arquitectura:

- contexto de la empresa;
- alcance de la solución;
- comparación de alternativas ERP;
- adecuación arquitectónica;
- riesgos y controles relacionados con la implementación.

### `decisiones/`

Contiene los **Architecture Decision Records (ADR)**. Cada ADR debe dejar trazabilidad de:

- contexto y problema;
- alternativas consideradas;
- decisión adoptada;
- justificación;
- consecuencias y riesgos;
- fuentes utilizadas.

Las decisiones pueden revisarse si aparece nueva evidencia. Un ADR no debe modificarse para ocultar una decisión anterior; cuando corresponda, debe actualizarse su estado o generarse una nueva decisión que la sustituya.

### `vistas/`

Contiene las representaciones visuales de la arquitectura.

Para C4 se separan:

```text
vistas/c4/
├── fuentes/   # archivos editables
└── render/    # resultados generados
```

Cuando se actualiza una fuente, debe regenerarse también el render correspondiente.

### `integraciones/`

Documentará las fronteras e integraciones entre sistemas cuando formen parte del alcance vigente. Hasta el parcial, la integración de mayor interés es la relación entre CRM y ERP.

No debe adelantarse una integración técnica cuando el incremento evaluado solo requiera una distinción conceptual.

### `versiones/`

Registra cambios relevantes de la arquitectura y permite explicar qué decisiones se mantienen, cuáles se ajustan y por qué.

## Criterios de documentación

Toda afirmación importante debe distinguir, cuando corresponda, entre:

- **evidencia o hecho verificado**;
- **interpretación del equipo**;
- **supuesto**;
- **vacío o pendiente**.

La arquitectura debe mantenerse coherente con los procesos, datos, producto y pruebas del repositorio.
