# Tratamiento de datos comerciales

## Metadatos

* **Fecha:** 17/10/2026
* **Versión:** 0.1
* **Autores:** Brenda Mirano
* **Custodio:** R-PRO
* **Alcance:** contexto comercial del CRM

## 1. Propósito

Definir criterios mínimos para utilizar información comercial de clientes y contactos sin recolectar datos que no tengan una finalidad clara.

Este documento es una **propuesta de gestión para el proyecto académico** y no constituye una auditoría legal exhaustiva de cumplimiento normativo.

## 2. Situación actual

- `[E][AS-IS]` Los números de clientes habituales suelen conservarse en los teléfonos utilizados por los propietarios. `[FN-02]`
- `[E][AS-IS]` No existe una nomenclatura uniforme de contactos ni una ficha central que reúna cliente, obra, maestro, dirección e historial. `[FN-02]`
- `[E][AS-IS]` Parte del contexto puede quedar distribuido entre conversaciones de WhatsApp y memoria de los propietarios. `[FN-02]`
- `[E][AS-IS]` MIGAL no utiliza actualmente esa base de números para campañas directas sistemáticas; responde principalmente a solicitudes del cliente. `[FN-02]`

## 3. Principio de finalidad

`[TO-BE]` Cada dato propuesto debe responder a una finalidad comercial concreta.

| Información | Finalidad principal |
|---|---|
| Nombre / razón social | Identificar correctamente al cliente |
| Teléfono | Comunicación operativa y seguimiento |
| Rol del contacto | Saber si es dueño, maestro, receptor u otro |
| Obra / dirección | Contextualizar cotización y futura coordinación |
| Canal / fuente | Comprender cómo inició la relación |
| Próxima acción | Evitar oportunidades abandonadas |
| DNI/RUC | Usarlo cuando sea pertinente para identificación o condición de comprobante |
| Historial de cotizaciones | Recuperar lo ofrecido y sus versiones |

## 4. Uso operativo vs. promocional

### Uso operativo

Puede comprender:

- responder una consulta iniciada por el cliente;
- elaborar o actualizar una cotización;
- hacer seguimiento de una solicitud comercial;
- coordinar información de una obra;
- recuperar antecedentes de una relación existente.

### Uso promocional

Comprende comunicaciones cuyo propósito principal sea marketing, promociones u ofertas no solicitadas.

`[TO-BE]` La propuesta diferencia ambos usos. Tener un número almacenado para atender una relación **no se interpreta automáticamente como consentimiento para campañas promocionales**.

## 5. Minimización

No se propone recolectar información “por si acaso”.

Ejemplos:

- Si una persona solo solicita un precio rápido, no es necesario completar una ficha fiscal extensa.
- DNI/RUC no se define como requisito universal de lead.
- Datos de dirección se registran cuando existe una necesidad asociada a obra, atención o futura entrega.
- Información que no tenga propósito comercial definido no debe agregarse al caso académico.

## 6. Datos en el repositorio académico

No deben publicarse:

- teléfonos reales;
- DNI/RUC reales de clientes;
- direcciones privadas reales;
- conversaciones privadas;
- información crediticia real;
- credenciales;
- cuentas bancarias;
- secretos o tokens.

Los casos y Excel del proyecto deben usar:

- datos sintéticos;
- identificadores ficticios;
- nombres explícitamente marcados como simulados.

## 7. Responsabilidad y actualización

`[TO-BE]` Quien atiende o mantiene la relación comercial debe actualizar el contexto cuando recibe información nueva relevante.

No se propone una sincronización automática ni un control técnico específico en esta etapa.

## 8. Vacíos

- `[ND]` Periodo formal de retención de datos comerciales.
- `[ND]` Procedimiento formal para retirar consentimiento promocional.
- `[ND]` Política interna aprobada de acceso a una futura ficha CRM.
- `[ND]` Reglas completas de conservación de conversaciones.

Estos puntos deben validarse antes de una implementación productiva.

## 9. Historial de cambios

| Versión | Fecha | Autor | Cambio |
|---|---|---|---|
| 0.1 | 17/10/2026 | Brenda Mirano | Versión inicial |
