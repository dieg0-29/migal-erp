# ADR 003: Adoptar módulos de contabilidad de terceros en Odoo Community

## 1. Metadatos
* **Fecha:** 25/09/2026
* **Estado:** Propuesto
* **Autores:** Brenda Mirano

## 2. Contexto y Problema
Ferre & Inversiones MIGAL requiere automatizar sus registros contables al realizar ingresos de inventario y registrar ventas (POS y mayoristas). El diseño arquitectónico exige que estos movimientos impacten directamente en la contabilidad general. Sin embargo, la versión Odoo V18 Community restringe el acceso al módulo de Contabilidad completo (asientos de doble partida, libros mayores), reservándolo exclusivamente para la versión Enterprise de pago. 

## 3. Restricciones de la Empresa (Drivers)
* **Presupuesto:** Capacidad nula para asumir costos recurrentes de licenciamiento por usuario (Enterprise).
* **Falta de personal TI:** No hay equipo técnico dedicado para desarrollar o mantener integraciones a medida mediante APIs con softwares externos.

## 4. Opciones Consideradas
* **Opción A (Odoo Enterprise):** Adquirir el licenciamiento oficial. Soluciona el problema de forma nativa, pero viola la restricción de presupuesto.
* **Opción B (Software externo):** Integrar un sistema contable de terceros (ej. un software local) vía API. Requiere desarrollo personalizado y mantenimiento constante, superando la capacidad del personal TI.
* **Opción C (Módulos de terceros/comunidad):** Instalar plugins de código abierto que desbloquean y añaden las funciones contables directamente en la versión Community.

## 5. Decisión
Decidimos adoptar la **Opción C**, integrando módulos de contabilidad gratuitos desarrollados por la comunidad (Odoo Community Association u Odoo Mates) dentro de nuestra instancia de Odoo V18 Community.

## 6. Justificación
Esta decisión equilibra las necesidades operativas con las severas restricciones de la empresa:
1. **Alineación con el presupuesto (Cero Costo):** Los módulos comunitarios desbloquean la capacidad contable esencial sin generar costos de licenciamiento, respetando el presupuesto bajo de la empresa.
2. **Viabilidad técnica (Cero integraciones externas):** Al instalarse de forma nativa dentro de la misma instancia de Odoo, se elimina la necesidad de programar integraciones complejas con otros sistemas.
3. **Automatización de los flujos TO-BE:** Permite que el POS y los movimientos de almacén (`stock.move`) disparen apuntes contables automáticos (débito/crédito), cumpliendo la precondición técnica establecida en los diagramas de componentes y flujos de procesos.
4. **Respaldo de la comunidad:** Se cuenta con el soporte de miles de desarrolladores de la Odoo Community Association (OCA), mitigando el riesgo de usar software sin mantenimiento.

## 7. Consecuencias (Trade-offs)
* **Positivas:** Cero costo de licenciamiento, despliegue más rápido y compatibilidad directa con los módulos nativos de Inventario y Ventas de Odoo.
* **Negativas / Riesgos:** Dependencia del soporte de terceros. Al cambiar a futuras versiones (ej. Odoo 19), se debe esperar a que la comunidad libere las actualizaciones de estos módulos contables antes de poder migrar.

## 8. Fuentes
* **[1]** Odoo Community Association (OCA) repositorio de herramientas financieras: https://github.com/OCA/account-financial-tools
* **[2]** Odoo Mates, Odoo 18 Community FREE Accounting: https://www.youtube.com/watch?v=XhZzgG7Q0Y0
