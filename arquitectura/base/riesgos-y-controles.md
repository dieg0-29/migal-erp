# Registro de riesgos y controles

## 1. Metadatos

* **Fecha:** 17/10/2026
* **Versión:** 0.1
* **Autores:** Diego Pinedo
* **Custodio:** R-PRO

## 2. Propósito

Reunir en un solo lugar los riesgos de la solución y sus controles. Los documentos de integración y de procesos pueden describir riesgos propios, pero se registran aquí con un ID único para darles seguimiento.

## 3. Registro

| ID | Riesgo | Señal temprana | Impacto | Control | Responsable | Evidencia | Origen | Estado |
|---|---|---|---|---|---|---|---|---|
| RSK-01 | Ampliar el alcance durante la implementación (Compras, automatizar WhatsApp) | Los propietarios piden módulos fuera del [alcance](alcance.md) | Retraso de la puesta en marcha | Toda ampliación se decide con un ADR y se registra en [versiones](../versiones/README.md) | R-PRO | ADR o registro de versión | Implementación | Abierto |
| RSK-02 | Stock registrado distinto del físico | Diferencias al preparar un pedido | Promesas incumplidas y pérdida de confianza en el sistema | Inventario físico antes de la carga inicial; ajustes autorizados ([SOD-03](../seguridad/modelo-autorizacion.md)); EXC-02 | R-ALM / R-PRO | Conteo y ajuste autorizado | Implementación, INT-01 | Abierto |
| RSK-03 | Diferencias entre comprobantes de KeyFacil y ventas registradas en Odoo | Descuadre en el cierre de caja | Problemas tributarios y retrabajo | Conciliación diaria de referencias y montos ([RN-11](../../procesos/catalogo-reglas.md)) | R-FAC | Cierre de caja conciliado | Implementación, INT-01 | Abierto |
| RSK-04 | Baja adopción: las ventas siguen en talonarios | Ventas del punto de venta menores que las ventas reales del día | El sistema queda desactualizado | Retirar progresivamente los talonarios y revisar el uso semanalmente | R-PRO | Reporte semanal de uso | Implementación | Abierto |
| RSK-05 | Caída de conexión o de luz en la tienda | El navegador no conecta con el servidor | No se pueden registrar ventas ni salidas | Contingencia con datos móviles; procedimiento de registro posterior; decidir alojamiento y respaldo (ADR pendiente) | R-PRO | Plan de contingencia | Implementación | Abierto |
| RSK-06 | Contactos duplicados por la atención en varios canales | Dos fichas para el mismo cliente | Condiciones distintas al mismo cliente | Búsqueda previa obligatoria ([RN-01](../../procesos/catalogo-reglas.md)) | R-ATN | Lead sin duplicados | INT-01 | Abierto |
| RSK-07 | Suponer controles automáticos que Odoo no aplica | Se documenta un bloqueo no probado | Controles inexistentes en la práctica | Probar cada control en la instancia antes de declararlo | R-PRO | Caso de prueba ejecutado | INT-01 | Abierto |
| RSK-08 | Sin responsable técnico (R-TEC) | Nadie gestiona usuarios, respaldos ni actualizaciones | Pérdida de datos o accesos indebidos | Asignar R-TEC o contratar soporte externo | R-PRO | Asignación documentada | [Modelo de autorización](../seguridad/modelo-autorizacion.md) | Abierto |
| RSK-09 | Precios de lista desactualizados en productos volátiles (cemento, fierro) | Ajustes frecuentes al cotizar | Cotizar con pérdida o precios inconsistentes | Lista de precios con fecha de vigencia mantenida por R-PRO (RN-03) | R-PRO | Historial de precios | [Justificación del CRM](../../procesos/comercial-crm/justificacion-crm.md) | Abierto |

## 4. Uso

* Un riesgo nuevo recibe el siguiente ID (RSK-nn) y se enlaza desde el documento que lo origina.
* El estado puede ser Abierto, Mitigado o Cerrado; un cierre necesita evidencia.

## 5. Historial de cambios

| Versión | Fecha | Autor | Cambio |
|---|---|---|---|
| 0.1 | 17/10/2026 | Diego Pinedo | Versión inicial; reúne los riesgos de implementación, de INT-01 y del CRM con perfiles del modelo de autorización |
