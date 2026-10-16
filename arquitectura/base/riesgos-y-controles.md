# Riesgos y Controles de la Implementación (Odoo V18)

Durante la planificación de la arquitectura ERP para Ferre & Inversiones MIGAL, se han identificado los siguientes riesgos y sus respectivas medidas de control, alineados a la estructura del proyecto:

| Riesgo | Señal temprana | Impacto | Control | Responsable | Evidencia |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Alcance** | Dueños solicitan incluir el módulo de compras o automatizar WhatsApp durante la implementación. | Retraso en los tiempos de la primera liberación. | Reafirmar los límites definidos en el ADR 001 y priorizar solo Inventario y Ventas. | Equipo de implementación | Acta de reunión de revisión |
| **Datos** | Diferencias visuales entre la pantalla de Odoo y la revisión física al preparar un pedido. | Pérdida de confianza en el sistema y descuadre contable (Kardex inexacto). | Realizar un inventario físico a puerta cerrada antes de la carga de `stock.quant`. | Jefe de Almacén | Reporte de ajuste de inventario validado |
| **Integración** | Clientes reportan montos distintos o hay descuadre en caja al fin del día por uso de Keyfacil y Odoo. | Problemas tributarios, de facturación y pérdida de tiempo. | Proceso de cierre de caja diario cruzando comprobantes de Keyfacil con salidas de Odoo. | Propietario / Cajero | Reporte de cierre de caja (Z) |
| **Adopción** | Baja cantidad de tickets generados en el POS comparado con las ventas físicas reales diarias. | El sistema ERP queda abandonado (ERP fantasma). | Retirar talonarios físicos y exigir el uso de Odoo POS como única vía de registro. | Propietarios | Reporte semanal de métricas de uso |
| **Continuidad / seguridad** | El navegador muestra error de conexión al servidor cloud o hay cortes de luz en el local de SMP. | Imposibilidad temporal de facturar o registrar salidas de almacén. | Uso de red de datos móviles (tethering) desde las tablets o celulares de los dueños. | Personal de tienda | Documento de plan de contingencia impreso |
