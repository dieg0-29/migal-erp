# Entregas

Esta carpeta conserva **snapshots de los hitos académicos presentados durante el curso**.

La documentación viva y vigente del proyecto se mantiene en `arquitectura/`, `procesos/`, `datos/`, `producto/`, `pruebas/` y `fuentes/`. Esta carpeta no debe convertirse en una segunda fuente de verdad.

## Estructura hasta el Examen Parcial

```text
entregas/
├── README.md
├── pc1/
├── pc2/
└── ep/
```

### Propósito

Cada subcarpeta puede conservar los archivos efectivamente presentados en un hito, por ejemplo:

- documento de entrega;
- presentación;
- versión exportada de diagramas;
- paquete final de evidencia;
- otros archivos requeridos por el docente.

## Reglas

- Conservar únicamente versiones que realmente correspondan a una entrega.
- Evitar nombres ambiguos como `final-final2`.
- Preferir nombres que indiquen hito y versión cuando sea necesario.
- No modificar retroactivamente una entrega histórica para que coincida con el estado actual del repositorio.
- Las correcciones posteriores deben realizarse en la documentación viva y registrarse en el `CHANGELOG.md`.

Ejemplo:

```text
entregas/pc2/
├── GE703_PC2_G1_MIGAL_v2.1.docx
└── presentacion-pc2.pdf
```

Los documentos del profesor o material de clase no deben almacenarse aquí como si fueran entregables del equipo.
