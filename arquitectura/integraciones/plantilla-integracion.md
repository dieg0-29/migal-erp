# INT-XX: <Sistema A> y <Sistema B> — <nombre corto>

> **Plantilla de integración funcional.** Describe procesos y responsabilidades, no contratos técnicos.
> Borra las notas `>` al completar el documento.

## 1. Metadatos

* **Fecha:** DD/MM/AAAA
* **Versión:** 0.1
* **Autores:**
* **Sistemas involucrados:** <Sistema A (módulos)>, <Sistema B (módulos)>

## 2. Propósito

> Qué problema de negocio resuelve la integración y por qué existe la frontera entre los sistemas.

En este documento, "evento" significa un suceso del proceso de negocio, no un mensaje técnico, una API ni un sistema de mensajería.

## 3. Alcance

### 3.1. Incluido

-

### 3.2. Excluido

-

## 4. Eventos de negocio

> Nombra los eventos en pasado y en lenguaje de negocio.

| ID | Evento | Disparador | Actor que registra | Sistema emisor | Sistema receptor | Regla o política | Datos necesarios |
|---|---|---|---|---|---|---|---|
| EV-01 | | | | | | | |

## 5. Fronteras de información

> Una ficha por cada punto donde la información pasa de un sistema a otro.

### F-01: <Sistema origen> a <Sistema destino>

* **Eventos activadores:** EV-XX
* **Descripción:**
* **Mecanismo actual:** Estándar del sistema | Configuración | Procedimiento manual | Externo con conciliación | Personalización futura | Por validar
* **Validaciones requeridas:**
  *

## 6. Supuestos y restricciones

-

## 7. Riesgos

| ID | Riesgo | Impacto | Mitigación |
|---|---|---|---|
| R-01 | | Alto / Medio / Bajo | |

## 8. Pendientes de validación

| ID | Pendiente | Frontera |
|---|---|---|
| P-01 | | F-XX |

## 9. Historial de cambios

| Versión | Fecha | Autor | Cambio |
|---|---|---|---|
| 0.1 | | | Versión inicial |

---

### Reglas de uso

1. Un documento por cada sistema que se integra, con todas sus fronteras (F-xx) dentro.
2. Una frontera se define entre sistemas, no entre módulos del mismo sistema.
3. Los IDs (EV, F, P, R) se numeran dentro del documento y sirven para referencias cruzadas.
4. Las fronteras se nombran con "a" (por ejemplo, "CRM a ERP"), sin flechas.
5. Toda mención a un documento del repositorio (ADR, reglas, procesos) se enlaza con una ruta relativa, por ejemplo `[ADR-004](../decisiones/ADR-004-....md)`.
6. Ningún comportamiento del sistema se da por hecho sin probarlo en la instancia real. Lo no probado se marca "Por validar".
