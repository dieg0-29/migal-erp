# Licencias y atribuciones de software y recursos de terceros

**Proyecto:** GE703 — Sistemas Integrados Empresariales · Grupo 1

**Caso de estudio:** Ferre & Inversiones MIGAL

**Fecha de consulta:** 16 de octubre de 2026

## Propósito y alcance

Este documento identifica las licencias y atribuciones de los componentes de software y recursos de terceros que aparecen en la documentación del proyecto. La identificación se apoya en los archivos del repositorio `migal-erp` y en las condiciones publicadas por sus integrantes. Su finalidad es asegurar que las referencias académicas sean verificables y que el equipo diferencie entre software seleccionado, herramientas de documentación y componentes efectivamente incorporados.

La elección arquitectónica de una herramienta no constituye evidencia de instalación, contratación o puesta en producción. Del mismo modo, la licencia general del repositorio no sustituye las licencias particulares de sus dependencias.

## Recursos identificados y atribución

| Recurso | Vinculación con MIGAL | Licencia o condición documentada | Atribución y fuente |
| --- | --- | --- | --- |
| Repositorio `migal-erp` | Almacena la documentación del proyecto, modelos y diagramas versionados. | **MIT**, conforme al archivo `LICENSE` del repositorio. | Titular indicado en el archivo: «Copyright (c) 2026 Diego». [Licencia del repositorio](https://github.com/dieg0-29/migal-erp/blob/main/LICENSE). |
| Odoo 18 Community Edition | Solución ERP propuesta en las decisiones arquitectónicas ADR-001 y ADR-002. | **LGPL, versión 3**. | Odoo S.A. [Licencias de Odoo 18](https://www.odoo.com/documentation/18.0/legal/licenses.html); [decisión sobre versión y edición](https://github.com/dieg0-29/migal-erp/blob/main/arquitectura/decisiones/ADR-002-version-y-edicion.md). |
| C4-PlantUML | Biblioteca incluida mediante referencias `!include` en las fuentes de los diagramas C4. | **MIT**. | Autores y colaboradores de C4-PlantUML. [Repositorio y licencia](https://github.com/plantuml-stdlib/C4-PlantUML); [diagramas fuente de MIGAL](https://github.com/dieg0-29/migal-erp/tree/main/arquitectura/vistas/c4/fuentes). |
| PlantUML | Lenguaje y herramienta asociados a los archivos `.puml` y diagramas C4 del proyecto. | Distribución predeterminada bajo **GPL-3.0-or-later**, con otras modalidades de licencia ofrecidas por el proyecto. | PlantUML y sus colaboradores. [Licencias oficiales](https://github.com/plantuml/plantuml/blob/master/LICENSES.md); [preguntas frecuentes](https://plantuml.com/faq). |

La documentación de PlantUML distingue la licencia de la herramienta de los derechos sobre los diagramas generados: las imágenes creadas mediante PlantUML pertenecen, en principio, a quienes elaboran las respectivas descripciones fuente, sin que la sola ejecución imponga la GPL a las imágenes. Esta precisión no exime de respetar licencias de bibliotecas, imágenes o materiales externos incorporados a una representación.

## Sistemas y alternativas referenciados

El repositorio también describe a **KeyFacil** como plataforma externa para comprobantes y **WhatsApp** como canal de comunicación con clientes. Ambos se identifican como servicios externos de la operación, sin que los archivos revisados documenten la incorporación de su código al repositorio. La bibliografía menciona otras soluciones ERP y alternativas contables que fueron consideradas durante el análisis. Su referencia académica no equivale a redistribución de software ni a contratación de licencias.

En particular, la arquitectura propone evaluar módulos contables comunitarios o de terceros para Odoo. Como no se acredita la instalación de un módulo específico, **no se atribuye una licencia definitiva a un complemento contable no identificado**. La licencia que corresponda deberá provenir del módulo concreto y su versión, no de una generalización sobre todo el ecosistema Odoo.

## Criterios de propiedad intelectual y publicación

El equipo conserva los avisos de licencia y atribución aplicables cuando utilice o distribuya archivos de terceros. Las fuentes externas se identifican mediante la organización responsable, el documento consultado y su enlace. En capturas, ilustraciones, diagramas y recursos gráficos se distingue el contenido elaborado por el grupo del contenido de otros titulares.

Los documentos de ejemplo deben utilizar información sintética o autorizada. La inclusión de una imagen, una biblioteca o una aplicación de terceros requiere revisar sus condiciones particulares cuando se redistribuya material protegido. Los datos, marcas o documentos externos citados con fines académicos no deben presentarse como creación propia.

## Referencias documentales

1. Grupo 1, [licencia `MIT` de `migal-erp`](https://github.com/dieg0-29/migal-erp/blob/main/LICENSE).
2. Grupo 1, [ADR-001, selección de ERP](https://github.com/dieg0-29/migal-erp/blob/main/arquitectura/decisiones/ADR-001-seleccion-erp.md), [ADR-002, versión y edición](https://github.com/dieg0-29/migal-erp/blob/main/arquitectura/decisiones/ADR-002-version-y-edicion.md) y [ADR-003, contabilidad](https://github.com/dieg0-29/migal-erp/blob/main/arquitectura/decisiones/ADR-003-contabilidad.md).
3. Odoo S.A., [Licenses — Odoo 18](https://www.odoo.com/documentation/18.0/legal/licenses.html).
4. C4-PlantUML, [repositorio oficial y licencia](https://github.com/plantuml-stdlib/C4-PlantUML).
5. PlantUML, [licencias](https://github.com/plantuml/plantuml/blob/master/LICENSES.md) y [preguntas frecuentes](https://plantuml.com/faq).
6. Grupo 1, [bibliografía técnica de MIGAL](https://github.com/dieg0-29/migal-erp/blob/main/fuentes/bibliografia.md).

**Criterio de interpretación:** este inventario consigna licencias identificadas y servicios referenciados. No certifica un despliegue operativo ni reemplaza la verificación de condiciones de un componente concreto antes de incorporarlo.
