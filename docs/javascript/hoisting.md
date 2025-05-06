---
hide:
  #- navigation
  - toc
---

<link rel="stylesheet" href="../../assets/stylesheets/javascript.css">

# **Hoisting: Entendiendo la Elevación en el Código**

El hoisting (o elevación) es un comportamiento en JavaScript que ocurre durante la fase de creación del contexto de ejecución. Este mecanismo permite que las declaraciones de variables y funciones sean “movidas” al inicio de su ámbito (scope) antes de que se ejecute el código. Aunque este fenómeno puede parecer confuso al principio, comprender cómo funciona el hoisting es clave para evitar errores y escribir código más predecible.

En este artículo exploraremos qué es el hoisting, cómo afecta las variables y funciones, y cómo utilizar este conocimiento para escribir un código más claro y eficiente.

## **¿Qué es el Hoisting en JavaScript?**

Cuando el motor de JavaScript ejecuta tu código, este pasa por dos fases:

  1. **Fase de creación**: Durante esta fase, el motor mueve las declaraciones de variables y funciones al inicio de su ámbito (scope) en memoria.
  2. **Fase de ejecución**: El código se ejecuta línea por línea, asignando valores a las variables y evaluando expresiones.

Este proceso de mover declaraciones al principio del ámbito es lo que se conoce como hoisting.

## **Hoisting de Variables**

El hoisting de variables depende del tipo de palabra clave utilizada para declararlas: `var`, `let` o `const`.

### **Variables declaradas con `var`**

Las variables declaradas con `var` son elevadas al inicio del ámbito y se inicializan con el valor `undefined`. Esto significa que puedes referenciar la variable antes de declararla, aunque su valor será `undefined` hasta que se asigne un valor explícito.

```js linenums="1" title="javascript"
console.log(counter); // undefined
var counter = 10;
console.log(counter); // 10
```

Durante la fase de creación, `counter` es declarada e inicializada con `undefined`. Durante la fase de ejecución, se asigna el valor `10` a `counter`.

**Código equivalente:**

```js linenums="1" title="javascript"
var counter;
console.log(counter); // undefined
counter = 10;
console.log(counter); // 10
```

### **Variables declaradas con let y const**

Las variables declaradas con `let` y `const` también son elevadas, pero no se inicializan. Esto significa que si intentas acceder a ellas antes de su declaración, obtendrás un error de referencia.

```js linenums="1" title="javascript"
console.log(counter); // ReferenceError: Cannot access 'counter' before initialization
let counter = 10;
```

Durante la fase de creación, `counter` se coloca en memoria, pero no se inicializa. Acceder a `counter` antes de su declaración genera un error.

## **Hoisting de Funciones**

El hoisting afecta tanto a las funciones como a las variables, pero funciona de manera diferente dependiendo de cómo se declaren las funciones. Es importante entender estos matices para evitar errores y aprovechar al máximo el comportamiento del lenguaje.

### **Declaraciones de funciones**

Las declaraciones de funciones son completamente elevadas. Esto significa que el motor de JavaScript mueve tanto la declaración como la definición de la función al inicio de su ámbito. Por lo tanto, puedes llamar a una función antes de declararla en el código.

```js linenums="1" title="javascript"
console.log(sumar(5, 10));

function sumar(a, b) {
    return a + b;
}
```

Durante la fase de creación, el motor eleva tanto el nombre de la función como su cuerpo completo al inicio del ámbito, esto permite que `sumar` sea accesible antes de que se declare en el código.

## **Expresiones de funciones y funciones flecha**

Las expresiones de funciones y las [funciones flecha](../arrow-functions/) (arrow functions) no son elevadas. Solo se eleva la declaración de la variable que las contiene, pero no la asignación de la función. Por lo tanto, intentar invocar una expresión de función o una función flecha antes de su definición genera un error.

```js linenums="1" title="javascript"
console.log(multiplicar(5, 2)); // TypeError: multiplicar is not a function

var multiplicar = function(a, b) {
    return a * b;
};
```

**Explicación:**

  - Durante la fase de creación, la variable `multiplicar` se eleva, pero se inicializa con `undefined`.
  - Cuando intentas llamar a `multiplicar` antes de asignarle la función, JavaScript arroja un error porque no es una función en ese momento.

### **Ejemplo con funciones flecha:**

```js linenums="1" title="javascript"
console.log(dividir(10, 2)); // ReferenceError: Cannot access 'dividir' before initialization

let dividir = (a, b) => a / b;
```

Las variables declaradas con `let` o `const` no se inicializan durante la fase de creación, aunque son elevadas. Esto provoca un error de referencia si intentas acceder a `dividir` antes de su declaración.

## **Ejemplo: Entendiendo el Hoisting**

Para comprender cómo funciona el hoisting en la práctica, veamos un ejemplo que combina el comportamiento de variables y funciones. Este ejemplo ilustrará cómo las declaraciones son elevadas al inicio del ámbito, cómo afectan las variables declaradas con `var`, `let`, y `const`, y qué sucede con las diferentes formas de declarar funciones.

```js linenums="1" title="javascript"
console.log(x); // undefined
var x = 5;

hoistedFunction(); // Función ejecutada correctamente

function hoistedFunction() {
    console.log("Hoisting de funciones");
}

nonHoistedFunction(); // Error: nonHoistedFunction is not a function

var nonHoistedFunction = function() {
    console.log("Esto no es hoisted");
};
```

**Explicación del ejemplo:**

  1. `x` es elevado e inicializado como `undefined`.
  2. La función `hoistedFunction` es elevada y completamente accesible.
  3. La variable `nonHoistedFunction` es elevada, pero su valor (la función) no se asigna hasta la fase de ejecución.

## **Buenas prácticas para evitar problemas con el Hoisting**

  1. **Usa `let` y `const` en lugar de `var`**: Estas palabras clave hacen que el comportamiento sea más predecible y evitan inicializaciones accidentales.
  2. **Declara funciones antes de usarlas**: Aunque las declaraciones de funciones son elevadas, es mejor organizarlas en un orden lógico.
  3. **Entiende el ámbito de las variables**: Asegúrate de comprender el ámbito (global o de bloque) donde se declaran tus variables.

***

### **Conclusión**

El hoisting es una característica poderosa de JavaScript que puede causar confusión si no se entiende completamente. Saber cómo funciona con variables (`var`, `let`, `const`) y funciones (declaraciones y expresiones) es fundamental para escribir código más claro y predecible. Siguiendo las buenas prácticas, puedes evitar errores comunes y aprovechar esta funcionalidad para estructurar mejor tu programa.

En el próximo artículo exploraremos cómo el ámbito de las variables influye en el comportamiento del código y su relación con el hoisting.

***

<br>
