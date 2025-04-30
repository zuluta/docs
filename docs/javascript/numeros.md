---
hide:
  #- navigation
  - toc
---

<link rel="stylesheet" href="../../assets/stylesheets/javascript.css">

# **Los Números**

En JavaScript el tipo de dato `number` se utiliza para representar tanto números enteros como decimales. Este tipo de dato es fundamental en la programación, ya que permite realizar operaciones matemáticas, trabajar con cálculos precisos y manejar valores especiales como `NaN`, `Infinity` y `-Infinity`.

## **¿Qué son los números en JavaScript?**

JavaScript utiliza un solo tipo de dato numérico (`number`) para representar todos los números, ya sean enteros o de punto flotante. A diferencia de otros lenguajes que tienen tipos distintos para enteros y decimales, JavaScript trata todos los números de la misma manera.

Técnicamente utiliza el formato IEEE-754 para el [tipo de dato `number`](../tipos-de-datos/), que cubre tanto enteros como valores de punto flotante. Sin embargo, con la especificación ES2020, se introdujo el tipo “bigint” para manejar enteros grandes, lo que proporciona una mayor flexibilidad en el manejo de valores numéricos en JavaScript.

### **Números Enteros**

A continuación se muestra cómo declarar una variable que contiene un número entero decimal:

```js linenums="1" title="javascript"
const counter = 100;
```

Los números enteros se pueden representar en los siguientes formatos:

  - Octal (base 8)
  - Hexadecimal (basado en 16)

Cuando utiliza números octales y hexadecimales en operaciones aritméticas, JavaScript los trata como números decimales.

### **Números Octales**

Un número literal octal comienza con el dígito cero (0) seguido de una secuencia de dígitos octales (números del 0 al 7). Por ejemplo:

```js linenums="1" title="javascript"
const num = 071;
console.log(num);
```

Si un número octal contiene un número que no está en el rango de 0 a 7, el motor de JavaScript ignora el 0 y trata el número como un decimal. Por ejemplo:

```js linenums="1" title="javascript"
const num = 080;
console.log(num);
```

Este comportamiento implícito podría causar problemas. Por tal razón ES6 introdujo un nuevo literal octal que comienza con `0o` seguido de una secuencia de dígitos octales (de 0 a 7). Por ejemplo:

```js linenums="1" title="javascript"
const num = 0o71;
console.log(num);
```

### **Números Hexadecimales**

Los números hexadecimales comienzan con 0x o 0X seguidos de cualquier número de dígitos hexadecimales (del 0 al 9 y de la a a la f). Por ejemplo:

```js linenums="1" title="javascript"
const num = 0x1a;
console.log(num);
```

### **Números de Punto Flotante**

Para definir un número literal de punto flotante, se agrega un punto decimal seguido de al menos un número. Por ejemplo:

```js linenums="1" title="javascript"
const price = 9.99;
const tax = 0.08;
const discount = .05; // valido pero no recomendable
```

Cuando trabajas con números muy grandes puedes usar la notación científica. La notación E indica que un número se multiplica por 10 elevado a una potencia específica.

```js linenums="1" title="javascript"
const amount = 3.14e7;
console.log(amount);
```

La notación `3.14e7` significa que se toma `3.14` y se multiplica por .`10`^`7`^

Asimismo puedes utilizar la notación E para representar un número muy pequeño.

```js linenums="1" title="javascript"
const amount = 5e-7; 
console.log(amount); // 0.0000005
```

La notación `5e-7` significa que se toma `5` y se divide entre `10.000.000`.

Además, JavaScript convierte automáticamente cualquier número de punto flotante con al menos seis ceros después del punto decimal en notación electrónica. Por ejemplo:

```js linenums="1" title="javascript"
const amount = 0.0000005;
console.log(amount);
```

Los números de punto flotante tienen una precisión de hasta 17 decimales. Cuando realiza operaciones aritméticas con números de punto flotante a menudo obtiene el resultado aproximado.

## **Trabajar con el Constructor `Number()`**

Los valores numéricos en JavaScript se pueden crear usando su forma literal o con el constructor incorporado `Number()`. Puedes crear un objeto `Number` usando la palabra clave `new`, por ejemplo: `new Number(123)`. Sin embargo esto no es común, ya que los objetos `Number` no son primitivos y pueden causar confusión.

Una vez creado un valor numérico, podemos realizar operaciones aritméticas como sumas (`+`), restas (`-`), multiplicaciones (`*`) y divisiones (`/`). Además de la aritmética básica, JavaScript admite una gran variedad de funciones matemáticas, `como Math.abs()`, `Math.pow()` y `Math.round()`, que se pueden utilizar para realizar operaciones más complejas.

### **Conversión a Primitivos Numéricos:**

Más comúnmente, `Number()` se utiliza como una función para convertir valores a primitivos numéricos. Por ejemplo, `Number("123")` convierte el string `"123"` en el número primitivo `123`.

```js linenums="1" title="javascript"
const stringToNumber = Number("123")
console.log(stringToNumber)
```

### **Diferencias Entre Objeto y Primitivo:**

Un objeto `Number` (`new Number(123)`) y un primitivo numérico (`Number("123")`) son diferentes, el primero es un objeto y el segundo es un primitivo. Esto se puede verificar usando `typeof`

```js linenums="1" title="javascript"
const number1 = new Number(123);
const number2 = Number("123");

console.log(typeof number1);
console.log(typeof number2);
```

### `Number()` y `BigInt`

Cuando utilizas la función `Number()` para convertir un `BigInt` a un número, no se produce un error. Sin embargo, es importante tener en cuenta que puede haber pérdida de precisión si el `BigInt` es demasiado grande.

***

## **Comparación de valores numéricos**

En JavaScript, los valores numéricos también se pueden comparar utilizando operadores de comparación como `<`, `>`, `<=` y `>=`. Por ejemplo, el siguiente código comprueba si la variable `num` es menor que 50:

```js linenums="1" title="javascript"
const num = 40;

if (num < 50) {
 console.log("El número es menor que 50");
}
```

**Métodos y Propiedades Útiles:**

  - **`Number.isNaN()`**: Determina si el valor es NaN (**Not a Number**) o No se un numero.
  - **`Number.isFinite()`**: Determina si el valor es finito.
  - **`Number.isInteger()`**: Determina si un valor es un entero.
  - **`Number.MAX_SAFE_INTEGER`**: El máximo entero seguro en JavaScript.
  - **`Number.MIN_SAFE_INTEGER`**: El mínimo entero seguro en JavaScript.

## **Infinity**

En JavaScript, `Infinity` es un valor especial que representa números que son demasiado grandes para ser manejados por el lenguaje. El número más grande que JavaScript puede manejar es `1.7976931348623157e+308`.

```js linenums="1" title="javascript"
const hugeNumber = 2e308;
console.log(hugeNumber);
```

También hay un valor `-Infinity`, que se usa para números negativos que van por debajo de `-1.7976931348623157e+308`

```js linenums="1" title="javascript"
const hugeNumber = -2e308;
console.log(hugeNumber);
```

El valor de infinito también se puede obtener al dividir entre cero.

```js linenums="1" title="javascript"
let result = 10 / 0;
console.log(result);
```

## **NaN**

`NaN` es un valor de error que significa “**Not a Number**“. Se utiliza cuando se intenta realizar una operación y el resultado no es un valor numérico. Por ejemplo: Como cuando intentas multiplicar un string por un número, por ejemplo.

```js linenums="1" title="javascript"
const result = "Hola" * 5;
console.log(result);
```

Pero… el resultado devuelto por el operador `typeof` para `NaN`. Algo curioso que debemos tener en cuenta.

```js linenums="1" title="javascript"
console.log(typeof NaN);
```

## **Redondear y dar formato a los números**

JavaScript proporciona varias funciones para redondear y dar formato a los valores numéricos. La función `toFixed()` puede utilizarse para redondear un número a un número especificado de decimales. Por ejemplo, el siguiente código redondea la variable número a dos decimales:

```js linenums="1" title="javascript"
const number = 1.23456;
const roundedNumber = number.toFixed(2);

console.log(roundedNumber); 
```

En temas más avanzados, exploraremos en detalle las diversas propiedades disponibles para el tipo `number` en JavaScript.

***

### **Conclusión**

Los números en JavaScript ofrecen una amplia gama de funcionalidades para realizar operaciones matemáticas, trabajar con valores especiales y manejar grandes cantidades con precisión. Comprender sus particularidades y las herramientas disponibles es esencial para el desarrollo de aplicaciones robustas.

En el siguiente artículo exploraremos los [valores booleanos en JavaScript](../booleanos/), abordando su importancia en las condiciones y la lógica de programación.

***

<br>
