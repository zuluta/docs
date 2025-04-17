---
hide:
  #- navigation
  - toc
---

# 3. ¿Qué es una función de flecha? :material-bow-arrow:
Las **funciones flecha** permiten escribir funciones de manera más concisa y legible, especialmente cuando se trata de **funciones cortas o funciones de una sola línea**.

### :material-arrow-right-box: Sintaxis de una función flecha:
  - La sintaxis básica de una función flecha es la siguiente: ==() => {}==
    - {==()==} Se utiliza para pasarle atributos a una función
    - {===>==} Se define como función flecha, es una función anónima sin nombre
    - {=={}==} Se utiliza para envolver el cuerpo de la función
***
<br>

## **3.1. Tipos de funciónes:**
Antes de nada, veamos una **comparación entre diferentes tipos de funciones**, esto es de vital importancia para entender como funciona cada uno, en que se relacionan y en que situaciones es conveniente utilizar uno u otro.

### Ejemplo 1
En este ejemplo, vamos a comparar **4 tipos de función equivalentes** y ver **en que se diferencian**. Para ello, hemos utilizado una ==declaración de función==, una ==expresión de función==, una ==expresión de función flecha== y una ==expresión de función flecha conciso==. Ninguno incluye atributos.

### :material-code-braces-box: ==Declaración de función== (multilínea) + llamada:
  - Si **no contiene atributos**, ==los paréntesis== estarán vacíos, pero ==deben estar presentes==.
  - Al ser una **función multilínea**, ==las llaves deben estar presentes==.
  - Al ser una **declaración de función**, ==no lleva punto y coma al final==.

```js linenums="1"
function cliente() {
    console.log('¡Bienvenido!');
}

cliente(); // Salida: ¡Bienvenido!
```

### :material-code-braces-box: ==Expresión de función== (multilínea) + llamada:
  - Si **no contiene atributos**, ==los paréntesis== estarán vacíos, pero ==deben estar presentes==.
  - Al ser una **función multilínea**, ==las llaves deben estar presentes==.
  - Al ser una **expresión de función**, ==lleva punto y coma al final==.

```js linenums="1"
const cliente = function() {
    console.log('¡Bienvenido!');
};

cliente(); // Salida: ¡Bienvenido!
```

### :material-code-braces-box: ==Expresión de función flecha== (multilínea) + llamada:
  - Si **no contiene atributos**, ==los paréntesis== estarán vacíos, pero ==deben estar presentes==.
  - Al ser una **función multilínea**, ==las llaves deben estar presentes==.
  - Al ser una **expresión de función**, ==lleva punto y coma al final==.

```js linenums="1"
const cliente = () => {
    console.log('¡Bienvenido!');
};

cliente(); // Salida: ¡Bienvenido!
```

### :material-code-braces-box: ==Expresión de función flecha conciso== (monolínea) + llamada:
  - Si **no contiene atributos**, ==los paréntesis== estarán vacíos, pero ==deben estar presentes==.
  - Al ser una **función monolínea**, ==las llaves pueden omitirse==.
  - Al ser una **expresión de función**, ==lleva punto y coma al final==.

```js linenums="1"
const cliente = () => console.log('¡Bienvenido!');

cliente(); // Salida: ¡Bienvenido!
```

<br>

### Ejemplo 2
Veamos el segundo ejemplo, esta vez, le pasamos **1 atributo** en la función:

### :material-code-braces-box: ==función flecha== (multilínea) + ==1 atributo==:
  - Las **funciones flecha** ==con un solo atributo, los paréntesis pueden omitirse==.
  - Al ser una **función multilínea**, ==las llaves deben estar presentes==.
  - Al ser una **expresión de función**, ==lleva punto y coma al final==.

```js linenums="1"
const cliente = (nombre) => { // antes
    console.log(`${nombre}`);
};

const cliente = nombre => { // despues
    console.log(`${nombre}`);
};
```

### :material-code-braces-box: ==función flecha conciso== (monolínea) + ==1 atributo==:
  - Las **funciones flecha** ==con un solo atributo, los paréntesis pueden omitirse==.
  - Al ser una **función monolínea**, ==las llaves pueden omitirse==.
  - Al ser una **expresión de función**, ==lleva punto y coma al final==.

```js linenums="1"
const cliente = (nombre) => { console.log(`${nombre}`) }; // antes

const cliente = nombre => console.log(`${nombre}`); // despues
```

<br>

### Ejemplo 3
Veamos el tercer ejemplo, esta vez, le pasamos **1 argumento** en la llamada:

### :material-code-braces-box: ==función flecha== (multilínea) + ==1 argumento en la llamada==:

```js linenums="1"
const cliente = nombre => {
    console.log(`${nombre}`);
};

cliente('Roberto'); // Salida: Roberto
```

### :material-code-braces-box: ==función flecha conciso== (monolínea) + ==1 argumento en la llamada==:

```js linenums="1"
const cliente = nombre => console.log(`${nombre}`);

cliente('Roberto'); // Salida: Roberto
```

<br>

### Ejemplo 4
Veamos el cuarto ejemplo, a diferencia del segundo ejemplo, aqui le pasamos **2 atributos** en la función y **2 argumentos** en la llamada a la función.

### :material-code-braces-box: ==función flecha== + ==2 atributos== + ==2 argumentos==:
  - Las **funciones flecha** ==con mas de un atributo, los paréntesis deben estar presentes==.
  - Al ser una **función multilínea**, ==las llaves deben estar presentes==.
  - Al ser una **expresión de función**, ==lleva punto y coma al final==.

```js linenums="1"
const cliente = (nombre, apellido) => {
    console.log(`${nombre} ${apellido}`);
};

cliente('Roberto', 'Mendiburu'); // Salida: Roberto Mendiburu
```

### :material-code-braces-box: ==función flecha conciso== + ==2 atributos== + ==2 argumentos==:
  - Las **funciones flecha** ==con mas de un atributo, los paréntesis deben estar presentes==.
  - Al ser una **función monolínea**, ==las llaves pueden omitirse==.
  - Al ser una **expresión de función**, ==lleva punto y coma al final==.

```js linenums="1"
const cliente = (nombre, apellido) => console.log(`${nombre} ${apellido}`);

cliente('Roberto', 'Mendiburu'); // Salida: Roberto Mendiburu
```
***
<br>

## **3.2. Tipos de funciónes flecha:**
Las **funciones flecha** (arrow functions) son indudablemente una de las características más populares de **ES6** (EcmaScript 6). Ellas introducen una nueva forma de escribir **funciones concisas**. Es importante notar que **las funciones flecha son anónimas**, lo que significa que **no tienen nombre** y no se pueden utilizar como metodos ni constructores dentro de una clase.

### :material-arrow-right-box: Características:
  - **Siempre son expresiones**, a diferencia de `function` (que puede ser **expresión** o **declaración**).
  - Esto implica que siempre deberemos asignar la expresión a una variable (o una constante).
  - Existen **2 tipos de funciones flecha**:
    - ==Expresión de función flecha== (multilínea)
    - ==Expresión de función flecha conciso== (monolínea)
<br>

### :material-arrow-right-box: Expresión de función flecha (multilínea):
En este ejemplo, podemos observar cómo ==la **expresión de función flecha** elimina la necesidad de escribir la palabra clave **function**==. Le pasa **2 atributos ==(a, b)==** entre parentesis, le pone la ==**=>**== (flecha) y acaba la fila con la apertura de una ==**{**== (llave) que se cierra despues del cuerpo de la función, en una nueva línea con el cierre de una ==**}**== (llave).

Esta función, esta construido en bloque. Al no estar toda la función en una misma línea, se trataria de una ==**expresión de función flecha** (multilínea) y no obtendria las características de un conciso (monolínea)==.

```js title="ejemplo.js" linenums="1"
const sumar = (a, b) => {
    return a + b;
};

const resultado = sumar(2, 6);
console.log(resultado); // Salida: 8
```
<br>

**Ejemplo con 3 atributos y 3 argumentos** 👇
```js title="ejemplo.js" linenums="1"
const cliente = (nombre, apellido, telefono) => {
    return (`${nombre} ${apellido} ${telefono}`);
};

const resultado = cliente('Roberto', 'Mendiburu', '666-666-666');
console.log(resultado); // Salida: Roberto Mendiburu 666-666-666
```
<br>

### :material-arrow-right-box: Expresión de función flecha conciso (monolínea):
En este ejemplo, podemos observar cómo ==la **expresión de función flecha conciso** elimina la necesidad de escribir la palabra clave **function**, las **llaves {}** y la declaración **return**==, resultando en una **expresión más compacta**.

```js title="ejemplo.js" linenums="1"
const sumar = (a, b) => a + b;

const resultado = sumar(2, 6);
console.log(resultado); // Salida: 8
```
<br>

**Ejemplo con 3 atributos y 3 argumentos** 👇
```js title="ejemplo.js" linenums="1"
const cliente = (nombre, apellido, telefono) => (`${nombre} ${apellido} ${telefono}`);

const resultado = cliente('Roberto', 'Mendiburu', '666-666-666');
console.log(resultado); // Salida: Roberto Mendiburu 666-666-666
```
***
<br>

## **3.3. Análisis de función, función flecha y función flecha conciso:**

**Veamos un ejemplo con las 3 opciones** 👇

```js title="ejemplo.js" linenums="1"
// Opción 1:
// Declaración de función + 3 atributos - multilínea
function cliente(nombre, apellido, telefono) {
    return `${nombre} ${apellido} ${telefono}`;
}

const resultado_1 = cliente('Roberto', 'Mendiburu', '666-666-666');
console.log(resultado_1); // Salida: Roberto Mendiburu 666-666-666



// Opción 2:
// Expresión de función flecha + 3 atributos - multilínea
const cliente = (nombre, apellido, telefono) => {
    return `${nombre} ${apellido} ${telefono}`;
};

const resultado_2 = cliente('Roberto', 'Mendiburu', '666-666-666');
console.log(resultado_2); // Salida: Roberto Mendiburu 666-666-666



// Opción 3:
// Expresión de función flecha conciso + 3 atributos - monolínea
const cliente = (nombre, apellido, telefono) => `${nombre} ${apellido} ${telefono}`;

const resultado_3 = cliente('Roberto', 'Mendiburu', '666-666-666');
console.log(resultado_3); // Salida: Roberto Mendiburu 666-666-666
```

### 🕵️ Analicemos las diferencias:

![Image](../../images/devcamp/checkpoint-08/analisis-de-funciones.png)
<br>
<br>
