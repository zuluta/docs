---
hide:
  #- navigation
  #- toc
---

Javascript tiene un objeto llamado `Math` que nos permite realizar numerosas operaciones y funciones matemáticas a través de los métodos que tiene definidos. De una manera coloquial, podríamos decir que tenemos incorporada en Javascript una calculadora científica para utilizar cuando queramos en nuestro código.

## **Métodos estáticos**

><br>
> Nota: Tenga en cuenta que muchas de las funciones matemáticas tienen una precisión que es dependiente de la implementación. Esto significa que los diferentes navegadores pueden dar un resultado diferente, e incluso el mismo motor de JS en un sistema operativo o arquitectura diferente puede dar resultados diferentes.
>
><br>

### ==Math.abs(x)==

Devuelve el valor absoluto de un número.

### ==Math.acos(x)==

Devuelve el arco coseno de un número.

### ==Math.acosh(x)==

Devuelve el arco coseno hiperbólico de un número.

### ==Math.asin(x)==

Devuelve el arco seno de un número.

### ==Math.asinh(x)==

Devuelve el arco seno hiperbólico de un número.

### ==Math.atan(x)==

Devuelve el arco tangente de un número.

### ==Math.atanh(x)==

Devuelve el arco tangente hiperbólico de un número.

### ==Math.atan2(y, x)==

Devuelve el arco tangente del cuociente de sus argumentos.

### ==Math.cbrt(x)==

Devuelve la raíz cúbica de un número.

### ==Math.ceil(x)==

La función `Math.ceil()` devuelve el valor entero redondeado más alto.

Ejemplo:

```js linenums="1" title="javascript"
Math.ceil(0.95); // 1
Math.ceil(4); // 4
Math.ceil(7.004); // 8
Math.ceil(-0.95); // -0
Math.ceil(-4); // -4
Math.ceil(-7.004); // -7
```

### ==Math.clz32(x)==

Devuelve el número de ceros iniciales de un entero de 32 bits.

### ==Math.cos(x)==

Devuelve el coseno de un número.

### ==Math.cosh(x)==

Devuelve el coseno hiperbólico de un número.

### ==Math.exp(x)==

Devuelve Ex, donde x es el argumento, y E es la constante de Euler (2.718...), la base de los logaritmos naturales.

### ==Math.expm1(x)==

Devuelve ex - 1.

### ==Math.floor(x)==

La función `Math.floor()` devuelve el valor entero redondeado más bajo.

Ejemplo:

```js linenums="1" title="javascript"
Math.floor(55.59); // 55
Math.floor(59); // 59
Math.floor(-55.51); // -56
Math.floor(-51); // -51
```

### ==Math.fround(x)==

Devuelve la representación flotante de precisión simple más cercana de un número.

### ==Math.hypot([x[, y[, …]]])==

Devuelve la raíz cuadrada de la suma de los cuadrados de sus argumentos.

### ==Math.imul(x, y)==

Devuelve el resultado de una multiplicación de enteros de 32 bits.

### ==Math.log(x)==

Devuelve el logaritmo natural (log, también ln) de un número.

### ==Math.log1p(x)==

Devuelve el logaritmo natural de x + 1 (loge, también ln) de un número.

### ==Math.log10(x)==

Devuelve el logaritmo en base 10 de x.

### ==Math.log2(x)==

Devuelve el logaritmo en base 2 de x.

### ==Math.max([x[, y[, …]]])==

Devuelve el mayor de cero o más números.

### ==Math.min([x[, y[, …]]])==

Devuelve el más pequeño de cero o más números.

### ==Math.pow(x, y)==

Las devoluciones de base a la potencia de exponente, que es, baseexponent.

### ==Math.random()==

El método `Math.random()` es un excelente método integrado para producir números aleatorios. Cuando se ejecuta `Math.random()`, devuelve un número aleatorio que puede estar entre 0 y 1. Se incluye el 0 y se excluye el 1.

**1. Generando un número de punto flotante aleatorio entre 0 y 1**

```js linenums="1" title="javascript"
console.log(Math.random()); // 0.7069207248635578
console.log(Math.random()); // 0.765046694794209
console.log(Math.random()); // 0.14069121642698246
```

Los números devueltos serán diferentes cada vez. Esto se asumirá para todos los ejemplos siguientes; se producirán resultados diferentes en cada pasada.

Para obtener un número aleatorio entre un rango mayor, multiplique el resultado de `Math.random()` por un número.

**1. Rango del 0 al 10 con punto flotante:**

```js linenums="1" title="javascript"
const x = Math.random()*10;
console.log(x); // 4.133793901445541
```

**2. Rango del 0 al 10 entero:**

```js linenums="1" title="javascript"
const x = Math.trunc(Math.random()*10);
console.log(x); // 6
```

**3. Rango entre un mínimo y un máximo con punto flotante:**

```js linenums="1" title="javascript"
const min = 83.1;
const max = 193.36;

const x = Math.random()*(max - min)+min;
console.log(x); // 138.7879589229711
```

**4. Rango entre un mínimo y un máximo entero:**

```js linenums="1" title="javascript"
const min = 83;
const max = 193;

const x = Math.trunc(Math.random()*(max - min)+min);
console.log(x); // 104
```

**5. Rango entre 1 y un máximo entero:**

```js linenums="1" title="javascript"
const x = Math.ceil(Math.random()*31);

console.log(x);
// 24
```

Si necesitamos que el resultado incluya tanto al mínimo como al máximo, la siguiente función `getRandomIntInclusive()` lo consigue.

```js linenums="1" title="javascript"
function getRandomIntInclusive(min, max) {
  min = Math.ceil(min);
  max = Math.floor(max);
  return Math.floor(Math.random() * (max - min + 1) + min);
}

const resultado = getRandomIntInclusive(20, 140);
console.log(resultado); // 65

// Ahora, tanto el valor mínimo como el máximo están incluidos en el resultado.
```

### ==Math.round(x)==

La función `Math.round()` Devuelve el valor de un número redondeado al número entero más cercano.

Ejemplo:

```js linenums="1" title="javascript"
Math.round(55.549); // 56
Math.round(55.50); // 56
Math.round(55.49) // 55
Math.round(55); // 55
Math.round(54.9); // 55
Math.round(-55.55); // -56
Math.round(-55.551); // -56
Math.round(-55); // -55
Math.round(-55.1); // -55
```

### ==Math.sign(x)==

Devuelve el signo de la x, que indica si x es positivo, negativo o cero.

### ==Math.sin(x)==

Devuelve el seno de un número.

### ==Math.sinh(x)==

Devuelve el seno hiperbólico de un número.

### ==Math.sqrt(x)==

Devuelve la raíz cuadrada positiva de un número.

### ==Math.tan(x)==

Devuelve la tangente de un número.

### ==Math.tanh(x)==

Devuelve la tangente hiperbólica de un número.

### ==Math.toSource()== No estándar

Devuelve la cadena "Math".

### ==Math.trunc(x)==

La función `Math.trunc()` devuelve la parte entera de un numero removiendo cualquier dígito decimal (dígitos situados después de la coma).

Ejemplo:

```js linenums="1" title="javascript"
Math.trunc(13.37); // 13
Math.trunc(42.84); // 42
Math.trunc(0.123); //  0
Math.trunc(-0.123); // -0
Math.trunc("-1.123"); // -1
Math.trunc(NaN); // NaN
Math.trunc("foo"); // NaN
Math.trunc(); // NaN
```

***

<br>
