# Guía de contribución

Este documento define las convenciones mínimas para trabajar de forma ordenada en el repositorio de **Ferre & Inversiones MIGAL**. El objetivo es que cada cambio sea identificable, revisable y trazable sin añadir burocracia innecesaria.

## 1. Flujo de trabajo

No trabajar directamente sobre `main`.

Flujo recomendado:

```text
main
  ↑
Pull Request
  ↑
rama de trabajo
```

Antes de crear una rama:

```bash
git checkout main
git pull origin main
git checkout -b <tipo>/<descripcion-corta>
```

Una rama debe representar **un objetivo principal**. Cuando el Pull Request sea integrado, la rama debe eliminarse.

## 2. Convención de ramas

Formato:

```text
<tipo>/<descripcion-corta>
```

| Tipo | Uso |
|---|---|
| `docs/` | Documentación, procesos, arquitectura y fuentes |
| `feat/` | Nueva funcionalidad o capacidad implementada |
| `fix/` | Corrección de un error |
| `refactor/` | Reorganización sin cambiar el propósito funcional |
| `test/` | Casos o automatización de pruebas |
| `chore/` | Mantenimiento del repositorio o configuración |
| `data/` | Datos maestros, datasets o plantillas de importación |

Reglas:

- minúsculas;
- sin tildes;
- sin espacios;
- usar `kebab-case`;
- describir el cambio, no a la persona.

Ejemplos:

```text
chore/reorganizar-repositorio
docs/pc2-escenario-crm
docs/actualizar-sipoc-o2c
docs/corregir-c4-contenedores
data/catalogo-productos
test/caso-descuento-excepcional
feat/configurar-multi-almacen
fix/corregir-stock-disponible
```

## 3. Convención de commits

Formato recomendado:

```text
tipo(alcance): descripcion
```

Ejemplos:

```text
chore(repo): crear estructura base del proyecto
docs(arquitectura): reorganizar comparacion ERP y ADR
docs(c4): separar fuentes y renders
docs(procesos): incorporar SIPOC O2C
data(productos): agregar plantilla de catalogo
test(pc2): agregar caso de excepcion comercial
fix(readme): corregir rutas internas
```

Un commit debe representar **una unidad lógica de cambio**. No es necesario crear un commit por archivo, pero tampoco conviene agrupar cambios sin relación bajo mensajes como `avance`, `cambios` o `final`.

## 4. Pull Requests

### Título

Usar el mismo patrón:

```text
tipo(alcance): descripcion
```

Ejemplos:

```text
chore(repo): reorganizar estructura del proyecto acumulativo
docs(pc2): documentar escenario CRM previo al pedido
docs(o2c): incorporar SIPOC y reglas del macroproceso
docs(arquitectura): corregir niveles del modelo C4
```

### Descripción mínima

```markdown
## Qué cambia

Descripción breve del cambio.

## Por qué se realiza

Problema, requisito, evidencia o decisión que motiva el cambio.

## Cambios principales

- ...
- ...

## Archivos afectados

- `ruta/archivo.md`

## Evidencia / fuentes

Fuentes o referencias utilizadas, cuando corresponda.

## Supuestos y pendientes

- Supuesto:
- Pendiente:
- Fuera de alcance:

## Validación realizada

Cómo se comprobó el cambio.

## Impacto sobre otros artefactos

- [ ] Arquitectura
- [ ] Procesos
- [ ] Datos
- [ ] Producto
- [ ] Pruebas
- [ ] Fuentes
```

En cambios pequeños, las secciones pueden ser breves. El objetivo es que otra persona pueda comprender el cambio sin reconstruirlo a partir del diff.

## 5. Revisión

Antes del merge, solicitar al menos **una revisión de otro integrante** cuando el cambio sea relevante.

La revisión debe comprobar, según corresponda:

- coherencia con el alcance vigente;
- consistencia con otros artefactos;
- enlaces y rutas;
- fuentes y evidencia;
- diferenciación entre hechos, interpretaciones, supuestos y pendientes;
- ausencia de datos sensibles;
- actualización de renders cuando cambien diagramas.

Las revisiones también forman parte de la evidencia de colaboración del equipo.

## 6. Diagramas

Mantener, cuando sea posible:

```text
fuentes/  -> archivo editable
render/   -> resultado generado
```

Ejemplo:

```text
arquitectura/vistas/c4/
├── fuentes/
│   └── contexto.puml
└── render/
    └── contexto.png
```

Si se modifica el archivo fuente, debe regenerarse también su render.

## 7. Documentación y evidencia

Las decisiones relevantes deben distinguir claramente entre:

- **hecho/evidencia:** información respaldada por una fuente o validación;
- **interpretación:** conclusión razonada del equipo;
- **supuesto:** condición aún no validada;
- **pendiente o vacío:** información que todavía debe obtenerse.

No presentar supuestos como hechos.

Si una modificación afecta otros documentos, debe actualizarse el artefacto relacionado o registrarse explícitamente el pendiente.

## 8. Datos y privacidad

No subir al repositorio:

- contraseñas;
- tokens;
- llaves o secretos;
- credenciales;
- datos personales sensibles;
- información real de clientes que no esté autorizada.

Los datos de prueba deben ser sintéticos, anonimizados o expresamente autorizados.

## 9. Fuentes y uso de IA

Toda afirmación relevante que dependa de documentación externa debe poder rastrearse a su fuente.

El uso de IA debe declararse en `fuentes/uso-ia.md` cuando corresponda, indicando su propósito y manteniendo validación humana sobre el resultado incorporado.

## 10. Actualización del CHANGELOG

Actualizar `CHANGELOG.md` cuando el Pull Request introduzca un cambio relevante en:

- estructura del repositorio;
- alcance;
- decisiones arquitectónicas;
- procesos;
- datos o controles;
- producto;
- pruebas o evidencia;
- incorporación o eliminación de un artefacto importante.

No es necesario registrar allí correcciones menores de ortografía, formato o cambios triviales.

Cuando varios commits forman parte del mismo cambio lógico, deben resumirse como **una sola entrada comprensible** en el changelog.

## 11. Merge y limpieza

Antes de integrar un Pull Request:

- comprobar que el objetivo de la rama esté completo;
- resolver comentarios de revisión;
- actualizar enlaces y rutas afectadas;
- revisar si corresponde actualizar `CHANGELOG.md`;
- verificar que no existan archivos accidentales o sensibles;
- mantener el título del PR descriptivo.

Para ramas con commits intermedios poco útiles, puede utilizarse **Squash and merge** para mantener un historial limpio en `main`.

Después del merge, eliminar la rama.

## 12. Cambios estructurales

Las reorganizaciones grandes deben realizarse en una rama propia, por ejemplo:

```text
chore/reorganizar-repositorio
```

No mezclar una migración estructural grande con cambios funcionales o con el desarrollo de un entregable específico. Esto permite revisar por separado qué archivos se movieron y qué contenido realmente cambió.

## 13. Códigos e identificadores

Cada código pertenece a un solo documento dueño. Antes de crear un código nuevo, verificar que el prefijo no esté en uso y registrarlo en esta tabla. Al renombrar o eliminar un código, actualizar todos los documentos que lo citan.

| Código | Significado | Documento dueño |
|---|---|---|
| RN-nn, CT-nn | Reglas de negocio de todos los procesos y sus controles | [Catálogo de reglas](procesos/catalogo-reglas.md) |
| EXC-nn | Excepciones | [Catálogo de reglas](procesos/catalogo-reglas.md) |
| CAM-nn | Campañas | [Cuenta, contacto y canales](procesos/comercial-crm/cuenta-contacto-canales.md) |
| ETP-nn | Etapas del flujo comercial | [Flujo comercial](procesos/comercial-crm/flujo-comercial.md) |
| DQ-nn | Reglas de calidad de datos | [Reglas de calidad](datos/reglas-calidad.md) |
| TR-nn | Trazas de auditoría | [Plan de trazabilidad](datos/trazabilidad/plan-trazabilidad-auditoria.md) |
| CP-nn | Casos de prueba | [Caso normal](pruebas/casos/CP-01-caso-normal.md) (CP-01), [caso de excepción](pruebas/casos/CP-02-caso-excepcion.md) (CP-02) |
| R-xxx, PR-nn.nn, SOD-nn | Perfiles, permisos y segregación | [Modelo de autorización](arquitectura/seguridad/modelo-autorizacion.md) |
| INT-nn, EV-nn, F-nn | Integraciones, sus eventos y fronteras | [Integraciones](arquitectura/integraciones/INT-01-CRM-ERP.md); fuera del documento se citan como `INT-01/EV-03` |
| O2C-K, P2P-K, P2P-E/C | Indicadores y eventos de los macroprocesos | [Indicadores O2C](procesos/o2c/indicadores.md), [P2P](procesos/p2p/eventos-controles.md) |
| AC-nn, CV-nn | Criterios de aceptación de la rúbrica | [Criterios de aceptación](pruebas/criterios-aceptacion/criterios-crm.md) |
| RSK-nn | Riesgos | [Registro de riesgos](arquitectura/base/riesgos-y-controles.md) |
| ADR-nnn, VER-nn, CA-nn | Decisiones, versiones y ajustes de arquitectura | [Decisiones](arquitectura/decisiones/), [versiones](arquitectura/versiones/README.md) |
| CLI, CON, DIR, PRD, OPP, COT, DEC, PED, ENT, CPE, PAG, PROV | Identificadores de entidad (con `-SIM` en datos de prueba) | [Registro de identificadores](datos/trazabilidad/identificadores-y-linaje.md) |
