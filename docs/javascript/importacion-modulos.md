---
hide:
  #- navigation
  - toc
---

<link rel="stylesheet" href="../../assets/stylesheets/javascript.css">

# **Importación**

La importación en JavaScript permite que un módulo use funciones, variables o clases de otro módulo, proporcionando una forma clara de reutilizar y organizar el código. Al importar elementos de otros módulos, se mantiene una estructura modular donde cada archivo cumple una función específica dentro del proyecto.

Existen varios tipos de importaciones que permiten incorporar elementos de un módulo en otro de manera flexible y precisa. Dependiendo de las necesidades del proyecto, se puede optar por:

  - **Importaciones nombradas**
  - **Importaciones por defecto**
  - **Importaciones con alias**
  - **Importar el módulo completo**

Cada tipo de importación tiene ventajas y casos de uso específicos que ayudan a mantener el código modular y organizado. Así que veamos como funciona cada una.

## **Importación nombrada**

La importación nombrada permite importar uno o varios elementos específicos de un módulo. Es ideal para acceder a múltiples exportaciones de un archivo.

Para facilitar la comprensión, imaginemos una estructura de proyecto que ilustre cómo funcionan las importaciones:

``` title="estructura"
proyecto/
├── index.html
└── js/
    ├── app.js         # Archivo principal donde se importan los módulos
    ├── matematicas.js # Módulo que exporta funciones matemáticas
    └── saludo.js      # Módulo que exporta una función de saludo por defecto
```

**Ejemplo de Importación Nombrada**

Supongamos que tenemos un módulo `matematicas.js` que exporta dos funciones: `calcularArea` y `calcularCircunferencia`:

```js linenums="1" title="javascript"
export function calcularArea(radio) {
    return Math.PI * radio * radio;
}

export function calcularCircunferencia(radio) {
    return 2 * Math.PI * radio;
}
```

En el archivo `app.js`, se pueden importar ambas funciones usando la sintaxis de importación nombrada:

```js linenums="1" title="javascript"
// app.js
import { calcularArea, calcularCircunferencia } from './matematicas.js';

const area = calcularArea(5); // 78.54
const circunferencia = calcularCircunferencia(5); // 31.42

document.body.innerHTML = `
    <p>Área: ${area}</p>
    <p>Circunferencia: ${circunferencia}</p>
`;
```

Esta sintaxis importa `calcularArea` y `calcularCircunferencia` directamente en `app.js`, haciéndolas disponibles para su uso en el código.

## **Importación por Defecto**

Se usa cuando un módulo tiene un elemento principal que encapsula su funcionalidad. Este tipo de importación no requiere llaves {} y permite asignar cualquier nombre al importar.

**Ejemplo de Importación por Defecto**

En el módulo `saludo.js`, exportamos una función `saludar` como exportación por defecto:

```js linenums="1" title="javascript"
// saludo.js
export default function saludar(nombre) {
    return `Hola, ${nombre}!`;
}
```

Para importar `saludar` en `app.js`, no necesitamos llaves `{ }`:

```js linenums="1" title="javascript"
// app.js
import saludar from './saludo.js';

const mensaje = saludar("Carlos"); // Hola, Carlos!
document.body.innerHTML = `<p>${mensaje}</p>`;
```

Esta simplicidad en la importación es una de las ventajas de las exportaciones por defecto.

## **Importación con Alias**

El alias es útil para evitar conflictos de nombres cuando se importan elementos de varios módulos con nombres similares.

**Ejemplo de Importación con Alias**

En el siguiente ejemplo, renombramos `calcularArea` como `area` y `calcularCircunferencia` como `circunferencia` al importarlos en `app.js`:

```js linenums="1" title="javascript"
// app.js
import { calcularArea as area, calcularCircunferencia as circunferencia } from './matematicas.js';

const resultadoArea = area(5);
const resultadoCircunferencia = circunferencia(5);

document.body.innerHTML = `
    <p>Área (Alias): ${resultadoArea}</p>
    <p>Circunferencia (Alias): ${resultadoCircunferencia}</p>
`;
```

El uso de alias es especialmente útil cuando se importa código desde múltiples módulos que pueden tener nombres de funciones o variables similares.

## **Importación Agrupada**

La importación agrupada permite combinar varias importaciones de un módulo en una sola declaración, lo cual es útil para mejorar la organización del código en archivos que dependen de múltiples exportaciones.

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

y en el archivo de importaciones lo hacemos de la siguiente forma:

```js linenums="1" title="javascript"
// app.js
import * as matematicas from './matematicas.js';

const area = matematicas.calcularArea(5);
const circunferencia = matematicas.calcularCircunferencia(5);

document.body.innerHTML = `
    <p>PI: ${matematicas.PI}</p>
    <p>Área: ${area}</p>
    <p>Circunferencia: ${circunferencia}</p>
`;
```

Esta importación agrupada facilita el manejo de módulos con muchas exportaciones.

## **Importación de Todo el Módulo**

La importación de todo el módulo con `* as` permite acceder a todas las exportaciones de un módulo como propiedades de un solo objeto. Esto es útil cuando se necesita importar múltiples funciones y constantes bajo un mismo nombre.

**Ejemplo de Importación de Todo el Módulo**

```js linenums="1" title="javascript"
export const PI = 3.14159;

export function calcularArea(radio) {
    return PI * radio * radio;
}

export function calcularCircunferencia(radio) {
    return 2 * PI * radio;
}
```

Importacion:

```js linenums="1" title="javascript"
import * as matematicas from './matematicas.js';

console.log(matematicas.PI);                // Output: 3.14159
console.log(matematicas.calcularArea(5));    // Output: 78.53975
console.log(matematicas.calcularCircunferencia(5)); // Output: 31.4159
```

En el anterior ejemplo todas las exportaciones de `matematicas.js` están accesibles como propiedades de `matematicas`, lo cual es conveniente para acceder a múltiples funciones o variables desde un solo módulo.

## **Buenas prácticas al importar en JavaScript**

Es importante mantener ciertas buenas prácticas al importar en JavaScript

  1. **Usa alias para evitar conflictos de nombres**: Si importas funciones con nombres similares de diferentes módulos, utiliza alias para mantener la claridad.
  2. **Evita importar todo el módulo innecesariamente**: Importar el módulo completo (`import * as ...`) puede ser excesivo si solo necesitas unas pocas funciones. Esto mejora el rendimiento y la claridad.
  3. **Agrupa las importaciones relacionadas**: Mantén juntas las importaciones de un mismo módulo para mejorar la organización.
  4. **Evita dependencias circulares**: Diseña tus módulos para que no dependan unos de otros de manera recursiva, ya que esto puede causar errores difíciles de depurar.

***

### **Conclusión**

La importación en JavaScript es esencial para construir aplicaciones modulares y bien estructuradas. Al comprender las diferentes formas de importar y aplicar buenas prácticas, puedes mantener un código más limpio, eficiente y escalable. En el próximo artículo, profundizaremos en la Reexportación de Módulos, que simplifica la organización en proyectos complejos.

***

<br>
