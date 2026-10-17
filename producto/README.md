# Producto

Esta carpeta reúne los artefactos que representan **lo que se construye, configura o prepara para hacer reproducible la solución propuesta**.

Mientras `arquitectura/` explica el diseño, `producto/` contiene los elementos de implementación o configuración que materializan ese diseño.

## Estructura prevista

```text
producto/
├── README.md
├── backlog.md
└── odoo/
    ├── configuracion/
    ├── modulos/
    ├── importaciones/
    └── exportaciones/
```

### `backlog.md`

Mantiene los elementos de trabajo relevantes del producto mientras no sean gestionados completamente mediante Issues o Projects.

Cada elemento debe poder relacionarse con una necesidad, decisión o incremento del proyecto.

### `odoo/`

Contendrá únicamente artefactos propios del proyecto relacionados con Odoo, por ejemplo:

- parámetros o decisiones de configuración;
- módulos propios o adaptaciones;
- plantillas de importación;
- exportaciones necesarias para pruebas o evidencia.

No debe utilizarse para copiar el código fuente completo de Odoo.

## Criterios

Un artefacto debe entrar en `producto/` cuando sea parte de la construcción o reproducción de la solución, no solo de su explicación.

Cuando una configuración implemente una decisión arquitectónica o una regla de proceso, debe mantener referencia hacia el documento que la sustenta.

No se deben incorporar credenciales, archivos locales sensibles ni secretos de configuración.
