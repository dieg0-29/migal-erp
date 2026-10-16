# Maestro conceptual de clientes y contactos

**Estado:** TO-BE, revisión pendiente. PC2: organización comercial; no es modelo físico ni plantilla de importación.

## Entidades y relaciones

La cuenta representa al cliente responsable de la relación comercial. Contacto identifica interlocutores; obra/dirección conserva contexto reutilizable. No crear una cuenta distinta por cada canal ni tratar automáticamente al maestro como responsable del pago.

| Entidad | Identificador | Información mínima propuesta | Regla |
|---|---|---|---|
| Cuenta | id_cliente | Nombre/referencia, tipo, estado, responsable comercial | ID único y estable |
| Contacto | id_contacto | Nombre, rol, cuenta relacionada, medio operativo pertinente, estado | Relación explícita con cuenta; no confundir coincidencia de nombre con identidad |
| Dirección/obra | id_direccion | Cuenta, referencia de obra, ubicación y estado cuando se necesiten | Varias direcciones por cuenta; señalar dato pendiente |

DNI/RUC se registra cuando sea pertinente; no es obligatorio para toda consulta. Un teléfono compartido no prueba que dos fichas sean la misma persona. El modelo conceptual debe permitir validar casos de maestros vinculados a varias obras sin imponer cardinalidades no comprobadas en Odoo.

## Mantenimiento

La persona que atiende propone altas/correcciones; propietarios validan cambios sensibles o fiscales. Antes de crear, buscar por referencias disponibles y revisar coincidencias. Conservar ID anterior y motivo si se consolida un duplicado; no borrar historial comercial. Desactivar datos obsoletos sin perder operaciones relacionadas.

## Calidad y privacidad

Comprobar ID único, contactos/direcciones enlazados, roles reconocibles y finalidad del dato. Diferenciar uso operativo y consentimiento promocional; no inferir consentimiento por tener teléfono. Solo datos SIM en el repositorio.

## Ejemplo y aceptación

CLI-SIM-001 relaciona CON-SIM-001 y CON-SIM-002 con DIR-SIM-001 en el catálogo. La revisión debe recuperar responsable y maestro sin duplicar cuenta ni exigir datos fiscales ausentes. Queda pendiente validar el mantenimiento y la representación real en Odoo.

Referencias: [cuenta/contactos](../../procesos/comercial-crm/cuenta-contacto-canales.md), [diccionario](../diccionario/diccionario-datos.md), [privacidad](../privacidad/tratamiento-datos.md), [fuentes](../../fuentes/fuentes-negocio.md).
