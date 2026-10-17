# ERP Ferre & Inversiones MIGAL — Grupo 1

Repositorio acumulativo del proyecto de **GE703 · Sistemas Integrados Empresariales** aplicado a **Ferre & Inversiones MIGAL**. El objetivo es construir y validar progresivamente una arquitectura empresarial integrada que conecte procesos, datos, aplicaciones, controles y evidencia verificable.

## Sobre la empresa

Ferre & Inversiones MIGAL es una empresa del sector retail ferretero. Su operación combina atención en tienda con pedidos y consultas por WhatsApp o llamadas, y actualmente mantiene distintos registros manuales o no integrados para inventario, precios, ventas a crédito y seguimiento operativo.

La descripción detallada del negocio, productos, operación actual y sistemas utilizados se encuentra en:

- [`arquitectura/base/contexto-empresa.md`](arquitectura/base/contexto-empresa.md)

## Problema de integración

El proyecto parte de una problemática central: existen procesos e información distribuidos entre registros manuales, conocimiento de los propietarios y sistemas externos, lo que dificulta mantener trazabilidad y una visión consistente de la operación.

La arquitectura propuesta se desarrolla de forma incremental y actualmente toma **Odoo 18 Community** como plataforma ERP base, mientras **KeyFacil** continúa como sistema externo para facturación electrónica y **WhatsApp** como canal externo de comunicación.

Las decisiones y sus fundamentos se documentan en:

- [`arquitectura/base/comparacion-erp.md`](arquitectura/base/comparacion-erp.md)
- [`arquitectura/decisiones/`](arquitectura/decisiones/)
- [`arquitectura/vistas/`](arquitectura/vistas/)

## Alcance hasta el Examen Parcial

Hasta el parcial, el repositorio cubre cuatro incrementos principales:

1. **Arquitectura ERP base:** contexto empresarial, comparación de alternativas, decisiones arquitectónicas y vistas C4.
2. **Macroprocesos:** Order to Cash (O2C), Procure to Pay (P2P) y su relación con inventario.
3. **Gestión comercial y CRM:** cuenta, contacto, canal, lead, oportunidad, cotización y decisiones comerciales.
4. **Integración parcial:** consolidación de los incrementos anteriores para el Examen Parcial.

El proyecto continúa evolucionando durante el curso. La presencia de un artefacto en el repositorio puede representar análisis, diseño, propuesta, configuración, prueba o evidencia; no implica necesariamente una implementación productiva.

## Documentación principal

| Área | Ubicación | Contenido |
|---|---|---|
| Contexto y arquitectura base | [`arquitectura/base/`](arquitectura/base/) | Empresa, comparación ERP, riesgos y fundamentos |
| Decisiones | [`arquitectura/decisiones/`](arquitectura/decisiones/) | ADR y decisiones arquitectónicas |
| Vistas | [`arquitectura/vistas/`](arquitectura/vistas/) | Diagramas C4, fuentes editables y renders |
| Procesos | [`procesos/`](procesos/) | O2C, P2P, inventario y comercial/CRM |
| Producto | [`producto/`](producto/) | Backlog y artefactos de implementación |
| Fuentes | [`fuentes/`](fuentes/) | Bibliografía, uso de IA, licencias y evidencia |
| Seguridad y autorización | [`arquitectura/seguridad/`](arquitectura/seguridad/) | Modelo de autorización: permisos y segregación de funciones |
| Datos | [`datos/`](datos/) | Maestros, calidad, trazabilidad y datos de prueba |
| Pruebas | `pruebas/` | Casos, resultados, evidencias e incidencias |
| Entregas | `entregas/` | Snapshots de PC1, avances, PC2 y EP |

El `README.md` funciona como punto de entrada. La información detallada debe mantenerse en los documentos de cada área para evitar duplicidad y conservar una sola fuente de verdad por tema.

## Estructura del repositorio hasta el parcial

```text
migal-erp/
├── README.md
├── CHANGELOG.md
├── CONTRIBUTING.md
├── LICENSE
├── .gitignore
│
├── arquitectura/
│   ├── base/
│   ├── decisiones/
│   ├── vistas/
│   ├── integraciones/
│   ├── seguridad/
│   └── versiones/
│
├── procesos/
│   ├── mapa-nivel-1/
│   ├── o2c/
│   ├── p2p/
│   ├── inventario/
│   └── comercial-crm/
│
├── datos/
│   ├── maestros/
│   ├── trazabilidad/
│   └── pruebas/
├── producto/
├── pruebas/
├── fuentes/
└── entregas/
```

## Diagramas

Las vistas C4 separan el archivo editable del resultado generado:

```text
arquitectura/vistas/c4/
├── fuentes/
│   ├── contexto.puml
│   ├── contenedores.puml
│   └── componentes/
└── render/
    ├── contexto.png
    ├── contenedores.png
    └── componentes/
```

Cuando se modifica un archivo fuente, debe actualizarse también su render correspondiente.

## Contribución

El trabajo colaborativo se realiza mediante ramas y Pull Requests. No se recomienda trabajar directamente sobre `main`.

```text
main
  ↑
Pull Request
  ↑
rama de trabajo
```

Las convenciones de ramas, commits, Pull Requests, revisión, validación y actualización del changelog se encuentran en:

- [`CONTRIBUTING.md`](CONTRIBUTING.md)

## Trazabilidad y evidencia

Las decisiones relevantes deben distinguir, cuando corresponda:

- **hecho o evidencia verificada**;
- **interpretación del equipo**;
- **supuesto**;
- **vacío o pendiente de validación**.

Los cambios relevantes en la evolución del proyecto se registran en:

- [`CHANGELOG.md`](CHANGELOG.md)

## Integrantes

| Integrante | Rol de trabajo |
|---|---|
| Alejandro Flores | Facilitación |
| Brenda Mirano | Producto |
| César Joaquín | Procesos |
| Diego Pinedo | Arquitectura |
| Gabriel Martínez | Datos |
| Luis Núñez | Validación |

Los roles organizan el trabajo, pero las contribuciones deben quedar verificables mediante commits, Pull Requests, revisiones, modelos, fuentes, pruebas o validaciones.

## Licencia

Consultar [`LICENSE`](LICENSE).
