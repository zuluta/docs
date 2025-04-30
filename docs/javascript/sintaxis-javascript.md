---
hide:
  #- navigation
  - toc
---

<link rel="stylesheet" href="../../assets/stylesheets/javascript.css">

# **Sintaxis de JavaScript: Fundamentos y Elementos Clave**

La sintaxis de JavaScript define las reglas y estructuras que se deben seguir para escribir código válido. Es fundamental comprender los conceptos básicos para evitar errores y aprovechar al máximo las capacidades del lenguaje. En este artículo exploraremos los aspectos esenciales de la sintaxis de JavaScript, incluyendo declaraciones, identificadores, comentarios, expresiones y palabras reservadas.

## **Declaraciones en JavaScript**

Las declaraciones son instrucciones que indican al programa que realice una acción específica, como asignar un valor a una variable, llamar a una función o ejecutar un bucle. En JavaScript, las declaraciones generalmente terminan con un punto y coma (`;`), aunque no es obligatorio se recomienda para mejorar la legibilidad y evitar errores.

Las declaraciones son la base para construir cualquier lógica en JavaScript. Cada línea de código ejecutable en un programa se considera una declaración.

### **Ejemplo de Declaración:**

```js linenums="1" title="javascript"
const mensaje = "Hola, mundo";
console.log(mensaje);
```

En el ejemplo anterior la primera declaración asigna un valor a la variable `mensaje`, mientras que la segunda muestra el valor en la consola.

**Buenas prácticas**: Es recomendable seguir estas pautas para que el código sea más legible:


  - **Usar una declaración por línea**: Evita combinar múltiples declaraciones en una sola línea.
  - **Terminar cada declaración con un punto y coma (`;`)**: Aunque JavaScript puede interpretar las declaraciones sin él, es mejor incluirlo para prevenir errores en código más complejo.

## **Bloques en JavaScript**

Los bloques de código son secuencias de declaraciones agrupadas entre llaves {…}. Estos son comunes en las estructuras de control como los bucles y funciones, además estos permiten controlar el ámbito (scope) de las variables.

Los bloques permiten organizar el código en secciones manejables delimitando su ámbito. Esto es especialmente útil cuando se trabaja con estructuras de control, como condicionales y bucles para asegurar que el flujo del programa se comporte de manera esperada.

```js linenums="1" title="javascript"
const condicion = true;

if (condicion) {
  // Declaraciones dentro del bloque if
} else {
  // Declaraciones dentro del bloque else
}

while (condicion) {
  // Declaraciones dentro del bloque while
}
```

En el anterior snippet se muestra como los bloques ayudan a definir las acciones a realizar en diferentes condiciones o repeticiones.

><br>
> Es importante recordar que JavaScript utiliza el alcance léxico, lo que significa que las variables declaradas dentro de un bloque estarán disponibles solo dentro de ese bloque y de los bloques internos, pero no fuera de ellos.
>
><br>

## **Identificadores en JavaScript**

Los identificadores son nombres que se utilizan para referirse a variables, funciones, clases y otros elementos del programa. Estos deben seguir ciertas reglas de nomenclatura. Ejemplo: Deben comenzar con una letra, guion bajo (**`_`**) o signo de dólar (**`$`**) y pueden contener letras, números, guiones bajos y signos de dólar.

Elegir identificadores claros y descriptivos es importante para que el código sea fácil de entender. Además, es fundamental seguir las convenciones y reglas de nomenclatura para evitar errores.

**Ejemplo: Identificadores válidos:**

```js linenums="1" title="javascript"
let nombreUsuario = "Carlos";
let _resultado = 100;
let $totalVentas = 5000;
```

><br>
> Ten en cuenta que la letra inicial no se limita al conjunto de caracteres ASCII y puede incluir caracteres ASCII extendidos o Unicode, aunque no se recomienda su uso.
>
><br>

**Reglas importantes:**


  - Los identificadores son **sensibles a mayúsculas y minúsculas** (`variable` y `Variable` se consideran diferentes).
  - No se pueden utilizar **palabras clave reservadas** como identificadores, ya que están reservadas para funciones específicas del lenguaje.

## **JavaScript es Case Sensitive**

Los identificadores en JavaScript son **sensibles a mayúsculas y minúsculas**. Esto significa que el lenguaje trata las letras mayúsculas y minúsculas como caracteres diferentes. Por lo tanto, en el siguiente ejemplo los identificadores `message` y `Message` serían considerados dos variables distintas.

```js linenums="1" title="javascript"
var message = "Hola, esto es un mensaje.";
var Message = "Esto es otro mensaje.";

console.log(message);
console.log(Message);
```

Es importante recordar esta distinción al nombrar tus variables y al referenciarlas más adelante en tu código para evitar confusiones o errores inesperados.

## **Comentarios en JavaScript**

Los comentarios son partes del código que se ignoran durante la ejecución del programa. Se utilizan para documentar el código, explicar el propósito de ciertas secciones o anotar cosas que se deben hacer.

El uso de comentarios es una práctica común para mejorar la legibilidad del código y facilitar la colaboración entre desarrolladores, proporcionando una mejor comprensión del propósito de las instrucciones o dejando notas útiles.

### **Comentarios de Una Sola Línea:**

Para crear un comentario de una sola línea en JavaScript, simplemente debes añadir dos barras inclinadas (`//`) antes del texto que actuará como comentario.

```js linenums="1" title="javascript"
// Esto es un comentario de una sola línea
```

### **Comentarios de Bloque**

Para crear un comentario de bloque o de varias líneas en JavaScript, utilizamos una barra inclinada seguida de un asterisco (`/*`) para iniciar el comentario y añadimos un asterisco seguido de una barra inclinada (`*/`) para finalizarlo.

```js linenums="1" title="javascript"
/* 
  Esto es un comentario 
  de múltiples líneas 
*/
```

><br>
> Utilizar comentarios de manera efectiva puede ayudar a identificar rápidamente secciones clave del código y entender su propósito.
>
><br>

## **Expresiones en JavaScript**

Una expresión es cualquier combinación de valores, variables, operadores y funciones que se evalúa para producir un resultado. Las expresiones son esenciales en JavaScript ya que permiten realizar operaciones y evaluar condiciones.

Las expresiones son las piezas básicas y pueden ser tan simples como un valor numérico o tan complejas como una combinación de múltiples operadores y funciones.

### **Tipos Comunes de Expresiones:**

  1. **Expresiones aritméticas**: Las expresiones aritméticas son útiles para cálculos matemáticos, como sumar, restar, multiplicar o dividir.

```js linenums="1" title="javascript"
const suma = 5 + 3;
```

  2. **Expresiones lógicas**: Evalúan condiciones y devuelven valores booleanos (`true` o `false`). Son comunes en las estructuras de control, como `if`, `while` y `for`, donde las condiciones determinan el flujo de ejecución.

```js linenums="1" title="javascript"
const esMayor = 10 > 5;
```

  3. **Expresiones de asignación**: Permiten almacenar el resultado de una operación o valor en una variable para su uso posterior.

```js linenums="1" title="javascript"
const resultado = 20;
```

Básicamente las expresiones son la base de los cálculos, la lógica y la programación en general.

## **Palabras Clave y Palabras Reservadas**

JavaScript tiene palabras clave reservadas para usos específicos y exclusivos del lenguaje. Estas palabras no se pueden usar como nombres de variables, funciones o identificadores ya que están destinadas a funciones específicas, como declarar variables, definir funciones o controlar el flujo del programa.

La siguiente tabla muestra las palabras reservadas de JavaScript tal como se definen en ECMA-262:

| Claves                           |||
| :-------- | :---------- | :------- |
| break	    | case	      | catch    |
| continue  | debugger	  | default  |
| else	    | export	  | extends  |
| function  | if	      | import   |
| new	    | return	  | super    |
| throw	    | try	      | null     |
| void	    | while	      | with     |
| class	    | delete	  | finally  |
| in	    | switch	  | typeof   |
| yield	    | const	      | do       |
| for	    | instanceof  | this     |
| var       |             |          |

Además de las palabras clave reservadas, ECMA-252 también define una lista de futuras palabras reservadas que no se pueden utilizar como identificadores o nombres de propiedad:

| Claves                          |||
| :--------- | :--------- | :------ |
| enum	     | implements | let     |
| protected	 | private	  | public  |
| await	     | interface  | package |
| implements | public     |         |

Conocer las palabras clave es importante para evitar errores de sintaxis y comprender mejor las funciones internas del lenguaje.

***

### **Conclusión**

Comprender la **sintaxis de JavaScript** es fundamental para escribir código correctamente. Conocer los conceptos básicos como declaraciones, bloques, identificadores, comentarios, expresiones y palabras clave te permitirá avanzar con confianza en el aprendizaje de JavaScript. Estos fundamentos son esenciales para construir aplicaciones más complejas y aprovechar al máximo las capacidades del lenguaje.

En el siguiente artículo exploraremos las [variables en JavaScript](../variables/), cómo se declaran y gestionan, así como las diferencias entre `var`, `let` y `const`.

***

<br>
