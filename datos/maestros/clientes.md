# Clientes, contactos y direcciones de obra

## 1. Metadatos

* **Fecha:** 17/10/2026
* **Versión:** 0.1
* **Autores:** Brenda Mirano
* **Sistema dueño:** CRM
* **Custodio:** R-PRO

## 2. Propósito

La **cuenta** representa al cliente responsable de la relación comercial; el **contacto** identifica a cada interlocutor (dueño de obra, maestro, receptor); la **dirección u obra** conserva un contexto reutilizable. Evita crear una cuenta distinta por cada canal y tratar automáticamente al maestro como responsable del pago.

## 3. Campos

| Entidad | Campo | Uso | Obligatorio |
|---|---|---|---|
| Cuenta | id_cliente | Identidad estable | Sí |
| Cuenta | nombre_razon_social, tipo, estado, responsable comercial | Reconocer y asignar al cliente | Al identificar la cuenta |
| Cuenta | documento_identidad (DNI/RUC) | Operación o comprobante que lo requiera | No para leads ni cotizaciones (RN-07) |
| Contacto | id_contacto, id_cliente, nombre, rol, medio operativo, estado | Relación explícita con la cuenta | Al relacionar el contacto |
| Dirección / obra | id_direccion, id_cliente, referencia de obra, ubicación, estado | Contexto de la obra; varias por cuenta | Cuando exista una obra o entrega |

Un teléfono compartido no prueba que dos fichas sean la misma persona. Las definiciones están en el [diccionario de datos](../diccionario-datos.md).

## 4. Reglas de calidad aplicables

* DQ-01 identificadores únicos, DQ-02 relaciones existentes, DQ-03 cuenta y contacto coherentes y DQ-11 minimización ([reglas de calidad](../reglas-calidad.md)).
* RN-01 control de duplicados ([catálogo de reglas](../../procesos/catalogo-reglas.md)).
* Uso operativo frente a promocional: ver [tratamiento de datos](../tratamiento-datos.md).

## 5. Mantenimiento

| Acción | Perfil | Condición |
|---|---|---|
| Alta | R-ATN | Buscar antes por teléfono, nombre o documento y revisar coincidencias |
| Corrección de datos sensibles o fiscales | R-PRO | Valida el cambio |
| Consolidación de duplicados | R-PRO | Conservar el ID anterior y el motivo; no borrar historial comercial |
| Desactivación | R-PRO | Sin perder las operaciones relacionadas |

## 6. Ejemplo `[SIM]`

`CLI-SIM-001` (Rosa Elena Huamán Salcedo) relaciona a `CON-SIM-001` (dueña de obra) y `CON-SIM-002` (maestro de obra) con `DIR-SIM-001` (ampliación del tercer piso). La revisión debe recuperar responsable y maestro sin duplicar la cuenta ni exigir datos fiscales ausentes.

## 7. Pendientes

* Validar el mantenimiento y la representación de cuentas, contactos y obras en Odoo, sin imponer cardinalidades no comprobadas.

## 8. Historial de cambios

| Versión | Fecha | Autor | Cambio |
|---|---|---|---|
| 0.1 | 17/10/2026 | Brenda Mirano | Versión inicial con la plantilla de entidad |

Referencias: [cuenta, contacto y canales](../../procesos/comercial-crm/cuenta-contacto-canales.md), [fuentes](../../fuentes/fuentes-negocio.md).
