---
hide:
  #- navigation
  - toc
---

<link rel="stylesheet" href="../../assets/stylesheets/javascript.css">

# **¿Qué es JavaScript?**

JavaScript es un lenguaje de programación versátil y ampliamente utilizado en el desarrollo web. Este fue diseñado inicialmente para interactuar con elementos de páginas web y hoy día permite a los desarrolladores implementar aplicaciones complejas, incluso afueras del entorno web.

Dentro de los navegadores web, JavaScript consta de tres partes principales:

  - **ECMAScript**: proporciona la funcionalidad principal.
  - **DOM (Document Object Model)**: proporciona interfaces para interactuar con elementos en páginas web.
  - **BOM (Browser Object Model)**: proporciona la API para interactuar con el navegador web.

JavaScript es una poderosa herramienta para agregar interactividad y dinamismo a las páginas web, desempeñando un papel fundamental como la tercera capa de las tecnologías web estándar junto a HTML y CSS.

><br>
> Más allá de solo mejorar la funcionalidad de una página, JavaScript permite crear experiencias de usuario más ricas e inmersivas. Desde la validación instantánea de formularios hasta la creación de aplicaciones complejas y dinámicas, pasando por la visualización de datos en tiempo real y el desarrollo de interfaces de usuario interactivas. Las posibilidades con JavaScript son casi ilimitadas.
>
><br>

Con el advenimiento de bibliotecas y frameworks modernos como React, Angular y Vue.js entre otros, el desarrollo web con JavaScript ha alcanzado un nuevo nivel de sofisticación y eficiencia, permitiendo a los desarrolladores construir aplicaciones web más rápidas, escalables y estéticamente atractivas.

## **¿Cómo funciona JavaScript?**

Cuando una página web se carga en un navegador, el proceso de renderizado comienza con la descarga y análisis del HTML y el CSS asociados. Una vez que estos recursos se han descargado y analizado el navegador procede a ejecutar cualquier código JavaScript presente en la página. Esta etapa es la mas importante para la interactividad y dinamismo ya que permite que el sitio web responda a la interacción del usuario de manera activa.

Por ejemplo, JavaScript puede agregar o eliminar elementos del DOM en función de las acciones del usuario, como hacer clic en un botón o ingresar datos en un formulario. Además, el script puede manipular estilos CSS y realizar solicitudes de red para cargar datos adicionales, todo en tiempo real sin necesidad de recargar la página u aplicación.

### **Motores JavaScript**

El motor JavaScript es un componente esencial de los navegadores web, son el encargado de interpretar y ejecutar el código JavaScript. Está compuesto por un analizador para examinar el código, un compilador para convertirlo en código de máquina y un intérprete para ejecutar el código compilado.

Los navegadores utilizan diversos motores de JavaScript para ejecutar el código de manera eficiente. Algunos de los motores más destacados son **V8** en Chrome, **SpiderMonkey** en Firefox y **JavaScriptCore** en Safari.

Inicialmente los motores JavaScript se implementaban como intérpretes. Sin embargo, en la actualidad los motores modernos se basan comúnmente en compiladores (**_just-in-time_**) que convierten el código JavaScript en código de bytes para mejorar el rendimiento.

## **JavaScript: lado del cliente vs servidor**

JavaScript es un lenguaje de programación que se puede utilizar tanto en el cliente como en el servidor. Aquí tienes un resumen de las diferencias entre ambos:

### **JavaScript del Lado del Cliente (Client-Side):**

  - Se ejecuta en el navegador del usuario.
  - Se utiliza para crear interacciones dinámicas en la página web.
  - Ejemplos incluyen animaciones, formularios interactivos y contenido que cambia sin recargar la página.

### **JavaScript del Lado del Servidor (Server-Side):**

  - Se ejecuta en el servidor, en plataformas como Node.js.
  - Se utiliza para manejar solicitudes, interactuar con bases de datos y servir contenido dinámico al cliente.
  - Ejemplos incluyen autenticación de usuarios, operaciones con bases de datos y generación de páginas web dinámicas.

Ambos lados trabajan juntos para ofrecer una experiencia web completa y funcional.

## **Resumen de la historia de JavaScript**

JavaScript fue desarrollado por [Brendan Eich de Netscape en 1995](https://es.wikipedia.org/wiki/Brendan_Eich){:target="_blank"}, inicialmente conocido como Mocha y luego renombrado como LiveScript. Netscape decidió cambiar el nombre a JavaScript para aprovechar la popularidad de Java, coincidiendo con el lanzamiento de Netscape Navigator 2.

Netscape lanzó JavaScript 1.1 con Netscape Navigator 3, mientras que Microsoft presentó Internet Explorer 3 (IE 3) con su propia implementación llamada JScript. Esto dio lugar a dos versiones de JavaScript en el mercado.

En 1997, JavaScript 1.1 se propuso a la [European Computer Manufacturers Association (ECMA)](https://ecma-international.org/){:target="_blank"} para su estandarización. El Comité Técnico #39 (TC39) fue asignado para estandarizar el lenguaje, dando lugar a ECMAScript, una especificación para un lenguaje de secuencias de comandos multiplataforma.

ECMA-262 fue la norma resultante, y ECMAScript fue adoptado por la Organización Internacional de Normalización (ISO/IEC), estableciendo un estándar para el lenguaje de programación JavaScript moderno.

## **Primer vistazo del lenguaje**

El siguiente apartado ofrece una sólida introducción al código de JavaScript. Si aún no estás familiarizado con él, está bien. Tendrás la oportunidad de aprender en el próximo tutorial.

### **Declarar variables**

Para definir una [variable en JavaScript](../variables/) utilizamos la palabra clave `var`:

```js linenums="1" title="javascript"
var name = "James";
var age = 20;
```

JavaScript también introdujo una nueva forma de declarar variables con la palabra clave `let`:

```js linenums="1" title="javascript"
let x = 10;
let y = 20;
```

><br>
> Hablaremos más sobre las diferencias entre var y let en próximos tutoriales, pero por ahora es una buena práctica utilizar let para declarar variables.
>
><br>

### **Definir Funciones**

Para declarar una función en JavaScript, usamos la palabra clave `function`:

```js linenums="1" title="javascript"
function add(a, b) {
  return a + b;
}
```

Esta función `add()` toma dos argumentos y devuelve su suma. Para llamar a la función utilizamos la siguiente sintaxis:

```js linenums="1" title="javascript"
let x = 10;
let y = 20;

function add(a, b) {
  return a + b;
}
let result = add(x, y);

console.log(result);
```

En el anterior ejemplo pasamos las variables `x` y `y` como argumentos a la función `add()` y almacenamos el resultado en la variable `result`.

### **Condicionales**

JavaScript también nos proporciona declaraciones de condición como `if-else` y `switch`. Por ejemplo:

```js linenums="1" title="javascript"
function divide(a, b) {
  if (b === 0) {
    throw 'División por cero';
  }
  return a / b;
}
```

En esta función `divide()` verificamos si el denominador `b` es cero. Si es así, lanzamos una excepción. De lo contrario, devolvemos el resultado de `a/b`.

### **Arrays (Matrices)**

Para declarar un array en JavaScript, utilizamos la siguiente sintaxis:

```js linenums="1" title="javascript"
let items = [];
```

También puedes declarar un array con elementos iniciales:

```js linenums="1" title="javascript"
let items = [1, 2, 3];
```

Para iterar sobre los elementos del array, puedes usar un bucle `for`:

```js linenums="1" title="javascript"
let items = [1, 2, 3];

for (let i = 0; i < items.length; i++) {
  console.log(items[i]);
}
```

Alternativamente, puedes utilizar el bucle `for...of` introducido en ES6:

```js linenums="1" title="javascript"
let items = [1, 2, 3];

for(let item of items) {
    console.log(item);
}
```

Este ejemplo introductorio te ha dado un primer vistazo a algunos de los conceptos básicos de JavaScript. En los próximos tutoriales, profundizaremos aún más en el lenguaje y aprenderemos a utilizarlo de manera más efectiva.

A medida que la web continúa evolucionando, JavaScript se afianza como una herramienta fundamental en el desarrollo web moderno. Con su versatilidad y capacidades en constante expansión, este lenguaje de programación permite a los desarrolladores crear experiencias de usuario cada vez más ricas e interactivas, tanto en el lado del cliente como del servidor.

***

<br>
