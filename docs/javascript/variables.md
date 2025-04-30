---
hide:
  #- navigation
  - toc
---

<link rel="stylesheet" href="../../assets/stylesheets/javascript.css">

# **Variables**

Las variables son componentes importantes en JavaScript, ya que permiten almacenar y gestionar datos de manera eficiente. Al aprender a trabajar con variables se facilita el desarrollo de aplicaciones dinámicas y funcionales. En este artículo exploraremos el trabajo de variables con JavaScript, el cómo declararlas, asignarles valores y usarlas adecuadamente en el contexto de JavaScript.

## **¿Qué son las Variables?**

Las variables son contenedores que almacenan información que puede ser utilizada y modificada durante la ejecución de un programa. Actúan como etiquetas que hacen referencia a un valor, permitiendo que el código sea más dinámico y fácil de entender.

En JavaScript, existen tres palabras clave principales para declarar variables: `var`, `let` y `const`. Cada una con características específicas que se utilizan en diferentes escenarios.

## **Declaración de Variables**

Antes de poder utilizar una variable es necesario declararla. A partir de ES6 se introdujeron las palabras clave `let` y `const` para mejorar el manejo de variables en comparación con `var`.

### **Palabras Clave para Declarar Variables**


  1. **La sentencia `var`**: Se utiliza para declarar e inicializar variables con acceso en todo el programa. Estas pueden cambiar su valor y se elevan al inicio del programa.
  2. **La sentencia `let`**: Declaran variables accesibles solo dentro de su ámbito, como en funciones. Estas no se elevan al inicio del programa.
  3. **La sentencia `const`**: Se utiliza para declarar constantes cuyo valor no puede modificarse. Al igual que las variables let las constantes no se elevan al inicio del programa.

**Ejemplos de Declaración:**

```js linenums="1" title="javascript"
let nombre = "Carlos";
const edad = 30;
var pais = "España";
```

En este ejemplo `nombre` se declara con `let` para que su valor pueda cambiar, `edad` con `const` para mantenerla inmutable, y `pais` con `var`, aunque se recomienda el uso de `let` o `const`.

## **Nombres de Variables o Identificadores**

Los **identificadores** son los nombres que asignamos a las variables y estas deben seguir ciertas reglas para ser válidos en JavaScript:


  - Deben comenzar con una letra, guion bajo (**`_`**) o signo de dólar (**`$`**), no con un número.
  - Pueden contener letras, números, guiones bajos o símbolos de dólar.
  - Son sensibles a mayúsculas y minúsculas (**`variable`** y **`Variable`** son diferentes).
  - No deben coincidir con palabras reservadas del lenguaje, como **`function`** o **`return`**.

### **Buenas Prácticas al Nombrar Variables**

  1. **Usar camelCase**: Esto indica el comenzar con minúscula y cada nueva palabra con mayúscula (**`miVariableImportante`**).
  2. **Elegir nombres descriptivos**: Evitar nombres genéricos como **`x`** o **`data`** a menos que el contexto sea claro.

><br>
> JavaScript es un lenguaje escrito dinámicamente. Esto significa que no es necesario especificar el tipo de variable en la declaración como otros lenguajes de tipo estático como Java o C#
>
><br>

Al nombrar constantes y variables es fundamental elegir nombres descriptivos que reflejen claramente su propósito y función en el código. Esto ayuda a mejorar la legibilidad y comprensión del código tanto para ti como para otros desarrolladores que puedan trabajar con él en el futuro.

## **Inicialización de Variables**

La inicialización de una variable consiste en asignarle un valor en el momento de su declaración. Si una variable se declara sin inicializar su valor es `undefined`.

Una vez que has declarado una variable o una constante puedes inicializarla asignándole un valor. Esto se logra mediante el operador de asignación (**`=`**), seguido del nombre y el valor que deseas asignarle.

**Ejemplo de inicialización:**

```js linenums="1" title="javascript"
let saludo;
console.log(saludo);

saludo = "Hola, mundo";
console.log(saludo);
```

En este caso la variable `saludo` se declara pero no se inicializa hasta la segunda línea, donde se le asigna un valor.

Incluso podemos declarar y asignar múltiples variables al mismo tiempo, para esto separamos cada declaración con una coma (**`,`**).

```js linenums="1" title="javascript"
let saludo = "Hola",
    usuario = "Pedro",
    estatus = true;
```

## **Cambiar el Valor de una Variable**

Las variables declaradas con `let` o `var` pueden cambiar su valor durante la ejecución del programa. Sin embargo, las declaradas con `const` no pueden ser reasignadas.

**Ejemplo: Cambio de Valor:**

```js linenums="1" title="javascript"
let edad = 25;
edad = 26;  // Cambio de valor
console.log(edad);
```

## **Diferencias Entre Variables no Definidas y no Declaradas**

Es importante distinguir entre variables no definidas y no declaradas:

  - **Variable no definida**: Ha sido declarada pero no se le ha asignado ningún valor, por lo que su valor es `undefined`.
  - **Variable no declarada**: No ha sido definida en el código, lo que provoca un error al intentar acceder a ella.

**Ejemplo: variable no definida vs. no declarada:**

```js linenums="1" title="javascript"
let mensaje;

console.log(mensaje);  // Output: undefined
console.log(texto);  // Error: texto is not defined
```

## **Variables Constantes y Mutabilidad**

Las constantes declaradas con `const`, no permiten la reasignación del valor una vez que ha sido definido. Sin embargo, si el valor es un objeto o un array sus propiedades o elementos internos pueden ser modificados.

**Ejemplo de constante mutable:**

```js linenums="1" title="javascript"
const usuario = {
  nombre: "Ana",
  edad: 28
};

usuario.edad = 29;  // Esto es válido, ya que se modifica una propiedad, no la referencia
console.log(usuario.edad);
```
***

### **Conclusión**

Las variables en JavaScript son un componente esencial para gestionar datos en las aplicaciones. Comprender las diferencias entre `let`, `const` y `var`, así como las prácticas recomendadas para nombrarlas e inicializarlas, las base para escribir un código claro y eficiente.

En el siguiente artículo abordaremos las [diferencias específicas entre `var`, `let` y `const`](../var-let/), profundizando en sus características y mejores prácticas.

***

<br>
