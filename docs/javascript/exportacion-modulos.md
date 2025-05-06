---
hide:
  #- navigation
  - toc
---

<link rel="stylesheet" href="../../assets/stylesheets/javascript.css">

# **Exportación**

La exportación en JavaScript permite compartir variables, funciones y clases entre módulos, facilitando la reutilización del código y mejorando la organización de aplicaciones modernas. Introducida en ES6, la exportación estandariza el uso de módulos, haciéndolos más eficientes y fáciles de mantener. Este artículo explora los tipos de exportaciones, sus diferencias y las mejores prácticas para exportar código en JavaScript.

## **Concepto de Exportación en JavaScript**

Un módulo en JavaScript encapsula su código y limita el acceso a sus elementos a menos que sean exportados explícitamente. Esto evita conflictos de nombres y promueve un código más modular y organizado.

Los dos tipos principales de exportaciones son:

  1. **Exportación nombrada**: Permite exportar múltiples elementos de un módulo.
  2. **Exportación por defecto**: Designa un único elemento principal por módulo.

## **Exportación Nombrada**

La exportación nombrada se utiliza cuando se necesitan exportar múltiples valores de un mismo módulo. Cada elemento que se desea exportar se especifica con la palabra clave `export`, lo que permite que otros módulos lo importen usando su nombre exacto.

**Ejemplo Básico de Exportación Nombrada**: En este ejemplo, exportamos una constante y dos funciones de forma nombrada.

```js linenums="1" title="javascript"
// matematicas.js
export const PI = 3.14159;

export function calcularArea(radio) {
    return PI * radio * radio;
}

export function calcularCircunferencia(radio) {
    return 2 * PI * radio;
}
```

### **Exportación Nombrada Agrupada**

También es posible agrupar varias exportaciones en una sola declaración al final del archivo, lo que ayuda a organizar el código.

```js linenums="1" title="javascript"
const E = 2.718;
function calcularExponente(x) {
    return Math.pow(E, x);
}

export { E, calcularExponente };
```

Esta estructura mejora la claridad en archivos con muchas exportaciones, facilitando la búsqueda de todas las exportaciones en un solo lugar al final del módulo.

## **Exportación por Defecto**

La exportación por defecto permite designar un elemento principal de un módulo, lo que simplifica su importación. A diferencia de las exportaciones nombradas, solo puede existir una exportación por defecto en cada módulo.

```js linenums="1" title="javascript"
// saludo.js
export default function saludar(nombre) {
    return `¡Hola, ${nombre}!`;
}
```

La exportación por defecto es útil cuando un módulo tiene una función o clase principal que representa la funcionalidad esencial del archivo.

## **Diferencias entre exportación nombrada y por defecto**

Aunque ambos tipos de exportación permiten compartir elementos entre módulos, existen diferencias clave en su uso y sintaxis:

### **Características de la Exportación Nombrada**

  - **Permite múltiples exportaciones**: Es posible exportar varias funciones, constantes o clases de un módulo.
  - **Debe usar el nombre exacto**: Al importar se requiere el nombre con el que fue exportado.
  - **Renombrado Opcional**: Se puede renombrar el elemento al importarlo, lo cual ayuda a evitar conflictos de nombres.

```js linenums="1" title="javascript"
import { calcularArea as area, calcularCircunferencia } from './matematicas.js';
```

### **Características de la Exportación por Defecto**

  - **Una sola exportación**: Solo un valor puede ser exportado por defecto en un módulo.
  - **Sin llaves**: No es necesario usar { } al importar.
  - **Renombrado Automático**: Al importarlo, se le puede asignar cualquier nombre.

```js linenums="1" title="javascript"
import cualquierNombre from './saludo.js';
cualquierNombre("Ana");  // Output: ¡Hola, Ana!
```

Estas diferencias permiten que las exportaciones por defecto se usen para el elemento principal de un módulo, mientras que las exportaciones nombradas son ideales para exportar múltiples elementos secundarios.

## **Renombrado de exportaciones**

Renombrar exportaciones es útil para evitar conflictos o mejorar la claridad al importar en otros módulos. Esto se puede hacer tanto al exportar como al importar:

**Renombrado al Exportar**

```js linenums="1" title="javascript"
const velocidadLuz = 299792458;
export { velocidadLuz as c };
```

**Renombrado al Importar**

```js linenums="1" title="javascript"
import { c as velocidad } from './constantes.js';
// velocidad;  Output: 299792458
```

## **Reexportación de Módulos**

La reexportación permite exportar valores importados de otros módulos, creando puntos de acceso centralizados para módulos complejos. Esto es especialmente útil en archivos de índice (index.js) donde se desea centralizar la importación de varios módulos.

```js linenums="1" title="javascript"
// constantes.js
export const GRAVEDAD = 9.81;
export const PI = 3.14159;

// index.js
export { GRAVEDAD, PI } from './constantes.js';
```

Ahora puedes importar todo desde index.js:

```js linenums="1" title="javascript"
import { GRAVEDAD, PI } from './index.js';
```

## **Buenas prácticas al exportar en JavaScript**

Al exportar en JavaScript, es bueno mantener un código organizado y seguir algunas prácticas recomendadas para mejorar la mantenibilidad:

  1. **Usa exportaciones por defecto para el componente principal**: Si un módulo tiene una funcionalidad principal, usa la exportación por defecto.
  2. **Prefiere exportaciones nombradas para módulos complejos**: Si hay varias funciones o valores, es más claro usar exportaciones nombradas.
  3. **Evita exportaciones circulares**: Las dependencias circulares pueden causar errores difíciles de depurar. Diseña tus módulos para evitar estas dependencias.
  4. **Organiza las exportaciones**: Agrupa todas las exportaciones al final del archivo para mejorar la legibilidad.

***

### **Conclusión**

La exportación en JavaScript es una herramienta poderosa para organizar y compartir código entre módulos. Usar exportaciones nombradas y por defecto de manera adecuada permite construir aplicaciones modulares y escalables, mejorando la colaboración y el mantenimiento del código.

***

<br>
