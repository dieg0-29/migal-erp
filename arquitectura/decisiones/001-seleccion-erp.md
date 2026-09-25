# ADR 001: Adopcion de Odoo como ERP

## 1. Metadatos

- **Fecha:** 25/09/2026
- **Estado:** Propuesto
- **Autores:** Luis Nuñez

## 2. Contexto y Problema

Ferre & Inversiones MIGAL necesita centralizar la gestión de sus operaciones, principalmente ventas e inventario, debido a la existencia de registros manuales y procesos desconectados.

Ante esta necesidad se evaluaron **StarSoft, Odoo y Microsoft Dynamics 365**, considerando sus características técnicas, funcionales y su adecuación al contexto de la empresa.

## 3. Restricciones de la Empresa (Drivers)

- **Tamaño de la empresa:** 2 propietarios, 2 trabajadores, 1 tienda y 2 almacenes.
- **Personal TI:** No cuenta con personal dedicado exclusivamente a TI.
- **Gestión de inventario:** Se requiere centralizar el stock de la tienda y almacenes.
- **Integración:** Se busca reducir los reprocesos y conectar las operaciones de ventas e inventario.
- **Contexto peruano:** Se deben considerar los requerimientos tributarios y operativos del país.
- **Extensibilidad:** La solución debe permitir incorporar nuevas funcionalidades conforme aumenten las necesidades.
- **Implementación gradual:** Se busca implementar los procesos de manera progresiva.

## 4. Opciones Consideradas

| Opción | Descripción |
|---|---|
| **StarSoft** | ERP orientado al mercado peruano, con funcionalidades relacionadas con procesos empresariales y requerimientos tributarios locales. |
| **Odoo** | ERP modular y extensible, con funcionalidades para ventas, inventario e integración. |
| **Dynamics 365** | ERP empresarial integrado al ecosistema Microsoft, con capacidades para finanzas, ventas, compras, inventario y analítica. |

La comparación detallada se encuentra en `arquitectura/comparacion-erp.md`.

## 5. Decisión

Hemos tomado la decision de usar Odoo como el ERP para Ferre & Inversiones MIGAL.

Esta decision se tomo despues de evaluar **StarSoft, Odoo y Microsoft Dynamics 365**, considerando las necesidades actuales de la empresa, sus recursos disponibles y la posibilidad de ampliar el sistema progresivamente.

Odoo permite utilizar su edicion **Community**, que es gratuita y de codigo abierto, reduciendo la dependencia de licencias propietarias para la implementacion inicial. Ademas, cuenta con diferentes modulos para cubrir procesos como ventas, inventario, punto de venta y otras operaciones empresariales.

La seleccion de la version y edicion especifica de Odoo se documentara en una decision arquitectonica posterior.

## 6. Justificacion

La seleccion se realizó considerando los criterios definidos para la empresa y la información recopilada durante la comparación de las tres alternativas.

StarSoft presenta una orientación al mercado peruano, incluyendo funcionalidades relacionadas con procesos tributarios y facturación electrónica. Esto resulta relevante para una empresa que opera en Perú. Sin embargo, en la evaluación realizada se encontró una menor disponibilidad de documentación técnica pública para analizar en detalle aspectos como su arquitectura, extensibilidad e integraciones.

Microsoft Dynamics 365 presenta un ecosistema empresarial amplio, capacidades de integración y diferentes servicios dentro del ecosistema Microsoft. Esto permite cubrir procesos empresariales de mayor alcance, pero también implica una solución orientada a escenarios con mayores necesidades de gestión e infraestructura que las identificadas actualmente para la empresa.

Odoo presenta una estructura modular que permite implementar progresivamente aplicaciones como ventas, inventario y punto de venta dentro de una misma plataforma. Además, su edición Community es gratuita y de código abierto, lo que permite reducir los costos iniciales asociados a licencias propietarias. La plataforma también dispone de documentación técnica, APIs y una comunidad que facilita el desarrollo y adaptación de nuevos módulos.

Otro aspecto considerado es su capacidad de extensión mediante módulos y aplicaciones de terceros, además de la posibilidad de realizar desarrollos propios. Esto permite adaptar el sistema a requerimientos específicos sin tener que desarrollar todas las funcionalidades desde cero. Sin embargo, estos módulos deben ser evaluados antes de su incorporación, considerando principalmente su compatibilidad con la versión utilizada, dependencias, licencia, mantenimiento y disponibilidad de actualizaciones.

Por lo tanto, considerando el tamaño de la empresa, la ausencia de personal TI dedicado, la necesidad de una implementación gradual, la centralización de ventas e inventario y la posibilidad de ampliar el sistema mediante módulos y desarrollos propios, se seleccionó Odoo como la plataforma ERP sobre la cual se desarrollará la solución.

La evidencia y comparación utilizada para esta decisión se encuentra documentada en `arquitectura/comparacion-erp.md`.

## 7. Consecuencias (Trade-offs)

- **Positivas:** Implementación modular, centralización de información, integración entre procesos, posibilidad de utilizar módulos de terceros y capacidad de desarrollar funcionalidades propias.
- **Negativas / Riesgos:** Los módulos de terceros deben evaluarse por compatibilidad, dependencias, licencia y mantenimiento. Los desarrollos propios también generan una responsabilidad adicional de mantenimiento y actualización.

## Fuentes

- `arquitectura/comparacion-erp.md`
- [1] Odoo. Documentación oficial de Odoo 18:\
  https://www.odoo.com/documentation/18.0/

- [2] Odoo. Administración, ediciones y gestión de bases de datos en Odoo 18:\
  https://www.odoo.com/documentation/18.0/administration.html

- [3] Odoo. Documentación oficial para desarrolladores de Odoo 18:\
  https://www.odoo.com/documentation/18.0/developer.html

- [4] Odoo. Licencias de Odoo 18:\
  https://www.odoo.com/documentation/18.0/legal/licenses.html
