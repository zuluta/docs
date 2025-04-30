---
hide:
  #- navigation
  - toc
---

<link rel="stylesheet" href="../../assets/stylesheets/javascript.css">

# **Tipos de datos**

En JavaScript los tipos de datos son fundamentales para gestionar y manipular la información. Entender los diferentes tipos y cómo funcionan es esencial para escribir código eficiente. JavaScript tiene varios tipos de datos que se dividen en dos categorías principales: primitivos y de referencia. En este artículo, exploraremos cada tipo de dato en JavaScript, cómo funcionan y ejemplos prácticos para ilustrar su uso.

## **Conocer el Tipo de Dato en JavaScript**

JavaScript es un lenguaje de tipado dinámico, lo que significa que una variable puede contener valores de diferentes tipos sin estar vinculada a uno específico. Por ejemplo:

```js linenums="1" title="javascript"
let score = 10;      // score es un número
score = true;        // score ahora es un booleano
score = "ganador";   // score ahora es una cadena de texto
```

Por lo tanto es importante determinar el tipo actual del valor almacenado en una variable. Para hacerlo utilizamos el operador `typeof`.

```js linenums="1" title="javascript"
let score = 10;
console.log(typeof(score));

score = false; 
console.log(typeof(score));

score = "Hi";
console.log(typeof(score));
```

Ahora que sabemos identificar el tipo de dato de una variable, podemos conocer como estos están definidos en JavaScript. Comencemos con los primitivos:

## **Tipos de Datos Primitivos**

Los tipos primitivos son los más básicos y simples en JavaScript. Estos se caracterizan por ser inmutables, lo que significa que su valor no se puede cambiar una vez creado.

Los tipos de datos primitivos en JavaScript son: `null`, `undefined`, `boolean`, `number`, `string`, `symbol`, `bigint`

### **1. Tipo Indefinido: `undefined`**

El tipo de dato `undefined` es una propiedad del objeto global y se utiliza para representar una variable que se ha declarado pero a la que aún no se le ha asignado un valor. Es decir, representa la ausencia de un valor definido.

```js linenums="1" title="javascript"
let score;

console.log(score);
console.log(typeof score);
```

### **2. Tipo Nulo: `null`**

En JavaScript el valor `null` representa la ausencia intencional de un valor. Es uno de los valores primitivos y se utiliza cuando se quiere indicar que una variable no tiene un valor asignado o que está “vacía”.

```js linenums="1" title="javascript"
let score = null;

if (score === null) {
  console.log('Aun no tienes un score iniciado');
} else {
  console.log("Tu score es " + score);
}
```

A diferencia de `undefined`, `null` se asigna explícitamente a una variable como representación de la ausencia de valor.

### **3. Tipo Número: `number`**

El tipo de dato `number` incluye tanto números enteros como números decimales. En JavaScript no hay distinción entre números enteros e índices flotantes.

```js linenums="1" title="javascript"
const entero = 42;
const decimal = 3.14;
const negativo = -10;
```

**Casos especiales de `number`**

  - `Infinity`: Resultado de dividir un número por cero.
  - `-Infinity`: Resultado de dividir un número negativo por cero.
  - `NaN` (**Not a Number**): Indica que un valor no es numérico.

```js linenums="1" title="javascript"
console.log(1 / 0);
console.log(-1 / 0);
console.log("hola" * 2);
```

### **4. Tipo Cadena de Caracteres: `string`**

El [tipo de dato string](../string/) o cadena se utiliza para representar una secuencia de caracteres y es uno de los tipos de datos más utilizados en JavaScript. Se puede definir con comillas simples, dobles o acento grave para los **template literals**, que permiten interpolación de variables.

```js linenums="1" title="javascript"
let saludo = "Hola";
let nombre = 'Mundo';
let mensaje = `Hola, ${nombre}!`;  // Template literal

console.log(mensaje);
```

><br>
> Los tipos strings en JavaScript son inmutables, lo que quiere decir que no se pueden modificar una vez creadas. No obstante, puedes crear una nueva cadena a partir de una existente.
>
><br>

### **5. Tipo Booleano: `boolean`**

El tipo de dato `boolean` representa un valor lógico que puede ser `true` o `false` (verdadero / falso). Es comúnmente utilizado en condiciones y comparaciones.

```js linenums="1" title="javascript"
let esMayor = 10 > 5;  // true
let esIgual = 10 === "10";  // false
```

Es importante destacar que en JavaScript algunos valores se consideran “`falsy`” o equivalentes a `false` cuando se evalúan en un contexto booleano. Estos incluyen `0`, `-0`, `null`, `false`, `NaN`, `undefined` y un string vacio `""`.

Por otro lado, todos los demás valores se consideran “`truthy`” o equivalentes a `true`, incluyendo objetos, arreglos y cadenas no vacías.

### **6. Tipo Símbolo: `Symbol`**

El tipo `symbol` es un valor único e inmutable usado comúnmente como identificador para las propiedades de los objetos. Cada vez que se crea un `symbol` es único.

```js linenums="1" title="javascript"
let id1 = Symbol("id");
let id2 = Symbol("id");

console.log(id1 === id2);
```

La función `Symbol()` crea un nuevo valor único cada vez que se llama. Por lo tanto si intentamos comparar sus valores, obtendremos el valor booleano `false`:

```js linenums="1" title="javascript"
console.log(Symbol() == Symbol());
```

### **7. Tipo Bigint**

El tipo bigInt en JavaScript es un primitivo que se introdujo para representar números enteros más grandes que el valor máximo que puede manejar el tipo `Number` (que es `2^53 – 1`). A diferencia de los números regulares, estos pueden ser grandes y precisos.

```js linenums="1" title="javascript"
let pageView = 9007199254740991n;

console.log(typeof(pageView));
```

## **Tipos de Datos de Referencia**

Los tipos no primitivos también conocidos como tipos de referencia, son más complejos, estos pueden contener una colección de valores y tienen comportamientos más dinámicos. Estos incluyen: `objects` (Objetos, Fechas, Arrays y Funciones)

### **Objetos (`Object`)**

```js linenums="1" title="javascript"
let persona = {
  nombre: "Juan",
  edad: 30,
  saludar: function() {
    console.log("Hola, soy " + this.nombre);
  }
};

persona.saludar();
```

### **Funciones**

En JavaScript las [funciones son objetos ciudadanos de primera clase](../funciones-ciudadanos-primera-clase/), lo que significa que se pueden almacenar en variables, pasarlas como argumentos y devolverlas como resultado.

```js linenums="1" title="javascript"
function sumar(a, b) {
    return a + b;
}

console.log(sumar(5, 3));
```

### **Fechas (`Date`)**

El objeto `Date` se utiliza para trabajar con fechas y horas.

```js linenums="1" title="javascript"
const hoy = new Date();

console.log(hoy.toDateString());
```

***

## **Diferencias Entre Tipos Primitivos y Referenciados**

**Mutabilidad:**

  - Los **tipos primitivos** son inmutables. Modificar un valor primitivo crea un nuevo valor.
  - Los **tipos de referencia** son mutables. Cambiar una propiedad de un objeto afecta directamente el valor.

**Asignación y Comparación:**

  - Cuando se asigna un tipo primitivo, se copia el valor. Con los datos de tipos referencia, se copia la referencia en memoria.
  - Los tipos de referencia se comparan por su referencia, no por su contenido.

***

## **Conversión entre tipos de datos**

Una de las potentes características de JavaScript es su capacidad para convertir entre distintos tipos de datos. Esto puede hacerse utilizando las funciones de conversión incorporadas, como `Number()`, `String()` y `Boolean()`.

Estas funciones pueden utilizarse para convertir un valor de un tipo de datos en un valor de un tipo de datos diferente sin cambiar los datos subyacentes. Pero de esto hablamos en profundidad en otros tutoriales.

***

### **Conclusión**

Entender los **tipos de datos en JavaScript** es clave para manipular la información correctamente. Al aprender sobre los tipos primitivos y de referencia, así como sus diferencias, puedes evitar errores comunes y escribir código más robusto.

En el siguiente artículo nos sumergiremos en el manejo de [números en JavaScript](../numeros/), abordando operaciones matemáticas y trucos para trabajar con precisión.

***

<br>
