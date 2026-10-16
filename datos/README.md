# Datos

Esta carpeta concentra la documentación relacionada con los **datos que permiten integrar y reconstruir los procesos de MIGAL**.

No funciona únicamente como depósito de archivos CSV: también documenta definiciones, calidad, trazabilidad, privacidad y criterios para datos de prueba.

## Estructura prevista hasta el Examen Parcial

```text
datos/
├── README.md
├── maestros/
├── transaccionales/
├── diccionario/
├── calidad/
├── trazabilidad/
├── privacidad/
└── prueba/
```

### `maestros/`

Documenta entidades relativamente estables compartidas por diferentes procesos, por ejemplo:

- clientes;
- productos;
- proveedores;
- precios.

### `transaccionales/`

Documenta los datos que nacen y cambian durante la ejecución de los procesos, como cotizaciones, pedidos, movimientos, facturas o pagos cuando entren en el alcance correspondiente.

### `diccionario/`

Define de forma consistente los campos y conceptos utilizados por el proyecto.

Cada definición relevante debería indicar, cuando sea necesario:

- nombre;
- significado;
- tipo;
- origen;
- responsable;
- regla de validación;
- observaciones.

### `calidad/`

Registra reglas necesarias para que los datos sean utilizables y confiables, por ejemplo:

- obligatoriedad;
- unicidad;
- consistencia;
- vigencia;
- completitud.

### `trazabilidad/`

Documenta los identificadores y relaciones necesarios para reconstruir el recorrido de una operación entre procesos y sistemas.

### `privacidad/`

Registra criterios de tratamiento y protección de información sensible.

### `prueba/`

Contiene datos sintéticos, anonimizados o autorizados utilizados para validar escenarios del proyecto.

## Reglas

- No subir credenciales, secretos ni datos personales sensibles.
- No presentar datos simulados como información real de la empresa.
- Todo dato de prueba debe poder distinguirse de un dato operativo real.
- Los cambios en maestros o reglas de calidad deben revisarse contra procesos, arquitectura y pruebas.
