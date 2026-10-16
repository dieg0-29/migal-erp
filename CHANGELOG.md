# Changelog

Este archivo resume los **cambios relevantes del proyecto acumulativo**. No reemplaza el historial de Git ni registra cada commit: documenta cambios que afectan la estructura del repositorio, el alcance, las decisiones, los procesos, los datos, las pruebas o la evidencia del proyecto.

## 2026-10-16 — Reorganización y preparación hasta el Examen Parcial

### Añadido

- `CHANGELOG.md` para registrar la evolución relevante del proyecto.
- `CONTRIBUTING.md` con convenciones de ramas, commits, Pull Requests, revisión y validación.
- Estructura objetivo del repositorio hasta el Examen Parcial.
- Organización prevista para O2C, P2P, inventario, gestión comercial/CRM, datos, pruebas y entregas.

### Cambiado

- El `README.md` pasa a funcionar como portada e índice del proyecto, enlazando a la documentación detallada de cada área en lugar de duplicarla.
- Se normaliza la estructura del repositorio en los bloques `arquitectura/`, `procesos/`, `datos/`, `producto/`, `pruebas/`, `fuentes/` y `entregas/`.
- Se eliminan estructuras redundantes del tipo `archivo.md/archivo.md`.
- `contexto-empresa.md` pasa a `arquitectura/base/contexto-empresa.md`.
- `comparacion-erp.md` pasa a `arquitectura/base/comparacion-erp.md`.
- Los ADR se normalizan bajo `arquitectura/decisiones/` con nombres `ADR-00X-*`.
- Las vistas C4 se reorganizan en `arquitectura/vistas/c4/`, separando archivos editables en `fuentes/` y resultados generados en `render/`.
- `flujo-principal-ventas.md` pasa a `procesos/o2c/flujo.md`.
- `flujo-principal-inventarios.md` pasa a `procesos/inventario/flujo.md`.
- `backlog.md` pasa a `producto/backlog.md`.
- `declaracion-ia.md` pasa a `fuentes/uso-ia.md`.

### Pendiente después de la reorganización

- Actualizar enlaces relativos y referencias internas afectadas por el movimiento de archivos.
- Consolidar el mapa de procesos de nivel 1.
- Completar los artefactos O2C y P2P correspondientes al avance de macroprocesos.
- Incorporar el incremento comercial/CRM de PC2.
- Completar los elementos de Semana 7 y la integración parcial para el EP.
- Revisar el contenido técnico de los documentos migrados; mover o renombrar un archivo no implica que su contenido haya sido validado o corregido.

## Criterio de uso

Un cambio debe aparecer aquí cuando modifica de manera relevante el estado del proyecto. Los ajustes menores de redacción, formato o correcciones triviales pueden quedar únicamente en el historial de commits.
