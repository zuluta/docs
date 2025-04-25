---
hide:
  #- navigation
  #- toc
---

Las **funciones flecha** permiten escribir funciones de manera más concisa y legible, especialmente cuando se trata de **funciones cortas o funciones de una sola línea**.

### :material-arrow-right-box: Sintaxis de una función flecha:
  - La sintaxis básica de una función flecha es la siguiente: ==() => {}==
    - {==()==} Se utiliza para pasarle atributos a una función
    - {===>==} Se define como función flecha, es una función anónima sin nombre
    - {=={}==} Se utiliza para envolver el cuerpo de la función
<br>
<br>

  - Las funciónes flecha, pueden ser de varios tipos:
    - Multilínea
    - Monolínea

![Image](../../assets/images/devcamp/checkpoint-08/sintaxis-funcion-flecha.png)
==Una función flecha es simplemente una expresión de función compacta== frente a una **expresión de función tradicional**. A diferencia de una **declaración de función**, las de **expresión de función** ==siempre deben acabar en punto y coma==.
***
<br>

## **3.1. Tipos de funciónes:**
Antes de nada, veamos una **comparativa entre diferentes tipos de funciones**, esto es de vital importancia para entender como funciona cada uno, en que se relacionan y en que situaciones es conveniente utilizar uno u otro.

### Ejemplo 1
En este ejemplo, vamos a comparar **4 tipos de función equivalentes** y ver **en que se diferencian**. Para ello, hemos utilizado una ==declaración de función==, una ==expresión de función==, una ==expresión de función flecha== y una ==expresión de función flecha conciso==. Ninguno incluye atributos.

### :material-code-braces: ==Declaración de función== (multilínea) + llamada:
  - Si **no contiene atributos**, ==los paréntesis== estarán vacíos, pero ==deben estar presentes==.
  - Al ser una **función multilínea**, ==las llaves deben estar presentes==.
  - Al ser una **declaración de función**, ==no lleva punto y coma al final==.

```js linenums="1"
function cliente() {
    console.log('¡Bienvenido!');
}

cliente(); // Salida: ¡Bienvenido!
```

### :material-code-braces: ==Expresión de función== (multilínea) + llamada:
  - Si **no contiene atributos**, ==los paréntesis== estarán vacíos, pero ==deben estar presentes==.
  - Al ser una **función multilínea**, ==las llaves deben estar presentes==.
  - Al ser una **expresión de función**, ==lleva punto y coma al final==.

```js linenums="1"
const cliente = function() {
    console.log('¡Bienvenido!');
};

cliente(); // Salida: ¡Bienvenido!
```

### :material-code-braces: ==Expresión de función flecha== (multilínea) + llamada:
  - Si **no contiene atributos**, ==los paréntesis== estarán vacíos, pero ==deben estar presentes==.
  - Al ser una **función multilínea**, ==las llaves deben estar presentes==.
  - Al ser una **expresión de función**, ==lleva punto y coma al final==.

```js linenums="1"
const cliente = () => {
    console.log('¡Bienvenido!');
};

cliente(); // Salida: ¡Bienvenido!
```

### :material-code-braces: ==Expresión de función flecha conciso== (monolínea) + llamada:
  - Si **no contiene atributos**, ==los paréntesis== estarán vacíos, pero ==deben estar presentes==.
  - Al ser una **función monolínea**, ==las llaves pueden omitirse==.
  - Al ser una **expresión de función**, ==lleva punto y coma al final==.

```js linenums="1"
const cliente = () => console.log('¡Bienvenido!');

cliente(); // Salida: ¡Bienvenido!
```

<br>

### Ejemplo 2
Veamos el segundo ejemplo, esta vez, le pasamos **1 atributo** en la función.

### :material-code-braces: ==Función flecha== (multilínea) + ==1 atributo==:
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

### :material-code-braces: ==Función flecha conciso== (monolínea) + ==1 atributo==:
  - Las **funciones flecha** ==con un solo atributo, los paréntesis pueden omitirse==.
  - Al ser una **función monolínea**, ==las llaves pueden omitirse==.
  - Al ser una **expresión de función**, ==lleva punto y coma al final==.

```js linenums="1"
const cliente = (nombre) => { console.log(`${nombre}`) }; // antes

const cliente = nombre => console.log(`${nombre}`); // despues
```

<br>

### Ejemplo 3
Veamos el tercer ejemplo, esta vez, le pasamos **1 argumento** en la llamada.

### :material-code-braces: ==Función flecha== (multilínea) + ==1 argumento en la llamada==:

```js linenums="1"
const cliente = nombre => {
    console.log(`${nombre}`);
};

cliente('Roberto'); // Salida: Roberto
```

### :material-code-braces: ==Función flecha conciso== (monolínea) + ==1 argumento en la llamada==:

```js linenums="1"
const cliente = nombre => console.log(`${nombre}`);

cliente('Roberto'); // Salida: Roberto
```

<br>

### Ejemplo 4
Veamos el cuarto ejemplo, a diferencia del segundo ejemplo, aqui le pasamos **2 atributos** en la función y **2 argumentos** en la llamada a la función.

### :material-code-braces: ==Función flecha== + ==2 atributos== + ==2 argumentos==:
  - Las **funciones flecha** ==con mas de un atributo, los paréntesis deben estar presentes==.
  - Al ser una **función multilínea**, ==las llaves deben estar presentes==.
  - Al ser una **expresión de función**, ==lleva punto y coma al final==.

```js linenums="1"
const cliente = (nombre, apellido) => {
    console.log(`${nombre} ${apellido}`);
};

cliente('Roberto', 'Mendiburu'); // Salida: Roberto Mendiburu
```

### :material-code-braces: ==Función flecha conciso== + ==2 atributos== + ==2 argumentos==:
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
Las **funciones flecha** (arrow functions) son indudablemente una de las características más populares de **ES6** (EcmaScript 6). Ellas introducen una nueva forma de escribir ==funciones concisas==. Es importante notar que las **funciones flecha** ==son anónimas==, lo que significa que ==no tienen nombre== y ==no se pueden utilizar como metodos ni constructores dentro de una clase==.

### :material-arrow-right-box: Características:
  - Siempre son expresiones.
  - Siempre deberemos asignar la expresión a una variable.
  - Pueden ser de varios tipos:
    - ==Expresión de función flecha== (multilínea)
    - ==Expresión de función flecha conciso== (monolínea)
<br>

### :material-arrow-right-box: Expresión de función flecha (multilínea):
Esta función, esta construido en bloque. Al no estar toda la función en una misma línea, se trataria de una ==**expresión de función flecha** (multilínea) y no obtendria las características de un (monolínea)==.

  - Al ser una **expresión de función**, ==debe asignarse a una **variable**==.
  - La **expresión de función flecha** ==elimina la palabra clave **function**==.
  - Una **función flecha** ==con mas de un atributo, los **paréntesis** deben estar presentes==.
  - Al ser una **función multilínea**, ==las **llaves** deben estar presentes==.
  - Al ser una **función multilínea**, ==el **return** debe estar presente==.
  - Al ser una **expresión de función**, ==lleva **punto y coma** al final==.

### :material-code-braces: ==Función flecha== + ==2 atributos== + ==2 argumentos==:
```js linenums="1"
const sumar = (a, b) => {
    return a + b;
};

const resultado = sumar(2, 6);
console.log(resultado); // Salida: 8
```

### :material-code-braces: ==Función flecha== + ==3 atributos== + ==3 argumentos==:
```js linenums="1"
const cliente = (nombre, apellido, telefono) => {
    return `${nombre} ${apellido} ${telefono}`;
};

const resultado = cliente('Roberto', 'Mendiburu', '666-666-666');
console.log(resultado); // Salida: Roberto Mendiburu 666-666-666
```
<br>

### :material-arrow-right-box: Expresión de función flecha conciso (monolínea):
En este ejemplo, podemos observar cómo la **expresión de función flecha conciso** ==elimina la necesidad de escribir== la palabra clave ==function==, las llaves =={}== y la declaración ==return==, resultando en una **expresión más compacta**.

  - Al ser una **expresión de función**, ==debe asignarse a una **variable**==.
  - La **expresión de función flecha** ==elimina la palabra clave **function**==.
  - Una **función flecha** ==con mas de un atributo, los **paréntesis** deben estar presentes==.
  - Al ser una **función monolínea**, ==las **llaves** pueden omitirse==.
  - Al ser una **función monolínea**, ==el **return** puede omitirse==.
  - Al ser una **expresión de función**, ==lleva **punto y coma** al final==.

### :material-code-braces: ==Función flecha conciso== + ==2 atributos== + ==2 argumentos==:
```js linenums="1"
const sumar = (a, b) => a + b;

const resultado = sumar(2, 6);
console.log(resultado); // Salida: 8
```

### :material-code-braces: ==Función flecha conciso== + ==3 atributos== + ==3 argumentos==:
```js linenums="1"
const cliente = (nombre, apellido, telefono) => `${nombre} ${apellido} ${telefono}`;

const resultado = cliente('Roberto', 'Mendiburu', '666-666-666');
console.log(resultado); // Salida: Roberto Mendiburu 666-666-666
```
***
<br>

## **3.3. Análisis de funciones:**
Veamos una comparativa entre 3 tipos de funciones 👇

  - Opción 1: ==Función tradicional==
  - Opción 2: ==Función flecha==
  - Opción 3: ==Función flecha conciso==

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

### :material-vector-difference: Diferencias entre funciones:

![Image](../../assets/images/devcamp/checkpoint-08/analisis-de-funciones.png)
Las **funciones flecha** pueden componerse de ==más de una línea==, lo cual ya ==nos obligará a emplear las **llaves** y el **return**==.
***
<br>

## **3.4. Funciones con "this":**
La palabra clave "**this**" tendra efecto dentro de una función o clase que la envuelve. ==Utilizamos "**this**" para acceder a las distintas propiedades de una función o clase==.

Veamos el uso de "**this**" con diferentes tipos de funciones:

  - Ejemplo 1: ==Función de expresión== (multilínea)
  - Ejemplo 2: ==Función flecha== (multilínea)
  - Ejemplo 3: ==Función flecha conciso== (monolínea)

### Ejemplo 1
En este ejemplo, se crea una ==declaración de función== llamada **Factura** y se le pasa **1 atributo**. Dentro de esta función, se crea una ==función de expresión== referenciando a la ==variable **total** pasado por "**this**"==.

### :material-code-braces: ==Declaración de función== + ==función de expresión== + ==this== + ==1 atributo== + ==1 argumento==:
```js linenums="1"
function Factura(subTotal) {
  this.iva = 0.21;
  this.subTotal = subTotal;

  this.total = function() {
    return ((this.iva * this.subTotal) + this.subTotal);
  };
}

const totalFactura = new Factura(200);
console.log(totalFactura.total()); // Salida: 242
```
<br>

### Ejemplo 2
Veamos el segundo ejemplo, se crea una ==declaración de función== llamada **Factura** y se le pasa **1 atributo**. Dentro de esta función, (aqui viene la diferencia respecto al ejempo 1) se crea una ==función flecha== referenciando a la ==variable **total** pasado por "**this**"==.

### :material-code-braces: ==Declaración de función== + ==función flecha== + ==this== + ==1 atributo== + ==1 argumento==:
```js linenums="1"
function Factura(subTotal) {
    this.iva = 0.21;
    this.subTotal = subTotal;

    this.total = () => {
        return ((this.iva * this.subTotal) + this.subTotal);
    };
}

const totalFactura = new Factura(200);
console.log(totalFactura.total()); // Salida: 242
```
<br>

### Ejemplo 3
Veamos el tercer ejemplo, se crea una ==declaración de función== llamada **Factura** y se le pasa **1 atributo**. Dentro de esta función, se crea una ==función flecha conciso== referenciando a la ==variable **total** pasado por "**this**"==.

### :material-code-braces: ==Declaración de función== + ==función flecha conciso== + ==this== + ==1 atributo== + ==1 argumento==:
```js linenums="1"
function Factura(subTotal) {
    this.iva = 0.21;
    this.subTotal = subTotal;

    this.total = () => ((this.iva * this.subTotal) + this.subTotal);
}

const totalFactura = new Factura(200);
console.log(totalFactura.total()); // Salida: 242
```
==El uso de función flecha es limitada==, no se puede utilizar como metodo ni constructor dentro de una clase.
***
<br>

## **3.5. Objetos y métodos con "this":**
==Cuando se crea una función dentro de un **objeto**, esta función pasa a llamarse **método**==. El **método**, ==no incorpora la palabra clave **function**== ni tampoco hace falta referenciarla a una **variable** como ocurre en la **expresión de función**. ==Un **método** debe tener nombre, no puede ser anónimo==.

### Ejemplo 1
En este ejemplo, incorpora un método al objeto.

### :material-code-braces: ==Objeto== + ==método== + =="this"==:

```js linenums="1"
const usuario = {
    nombre: 'Roberto',
    apellido: 'Mendiburu',
    telefono: '333-666-666',

    mostrar() {
        console.log(this);
    }
};

usuario.mostrar();

/* Salida:

{
Nombre: Roberto
Apellido: Mendiburu
Teléfono: 333-666-666
mostrar: [Function: mostrar]
}

*/
```
<br>

Veámos que ocurre si ==cambiamos el **método** por una **función flecha**==:
```js linenums="1"
const usuario = {
    nombre: 'Roberto',
    apellido: 'Mendiburu',
    telefono: '333-666-666',

    () => {
        console.log(this);
    };
};

usuario; // no podemos llamar al método flecha porque no tiene nombre.

/* Salida:

SyntaxError

*/
```
Lo que ocurre aquí es que, al tratarse de una función anónima, no podemos llamarla de ninguna manera, por eso ==nos devuelve un error de sintaxis==.

  - Las **funciónes flecha**, ==no pueden ser usados como métodos, dentro de un objeto o clase==.
***
<br>

## **3.6. Objetos y funciones con "this":**
==Mostremos la diferencia== en cuanto al uso de "**this**" en las ==funciones tradicionales y las funciones flecha==.

### Ejemplo 1
En este ejemplo, incorpora una función como propiedad del objeto.

### :material-code-braces: ==Objeto== + ==función de expresión== + =="this"==:

```js linenums="1"
const cliente = { 
    nombre: 'Roberto',
    apellido: 'Mendiburu',
    
    nombreCompleto: function() {
        console.log("this es: ", this); 
        console.log(`Cliente: ${this.nombre} ${this.apellido}`);
    }
};


cliente.nombreCompleto();

/* Salida:

this es: {
    nombre: 'Roberto',
    apellido: 'Mendiburu',
    nombreCompleto: [Function: nombreCompleto]
}   
Cliente: Roberto Mendiburu

*/
```
<br>

Veámos que ocurre si sacamos a la función fuera del objeto:
```js linenums="1"
const cliente = { 
    nombre: 'Roberto',
    apellido: 'Mendiburu'
};

const nombreCompleto = function() {
    console.log("this es: ", this); 
    console.log(`Cliente: ${this.nombre} ${this.apellido}`);
};


nombreCompleto(cliente);

/* Salida:

this es:  Object [global] {etc.}
Cliente: undefined undefined

*/
```
Nos devuelve un resultado distinto.

  - El "**this**" hace ==referencia al objeto global== (window) ya que no tiene al objeto anterior envolviendolo.

<br>

### Ejemplo 2
En este ejemplo, incorpora una función flecha como propiedad del objeto.

### :material-code-braces: ==Objeto== + ==función de expresión flecha== + =="this"==:
```js linenums="1"
const cliente = { 
    nombre: 'Roberto',
    apellido: 'Mendiburu',
    
    nombreCompleto: () => {
        console.log("this es: ", this); 
        console.log(`Cliente: ${this.nombre} ${this.apellido}`);
    }
};


cliente.nombreCompleto();

/* Salida:

this es:  {}
Cliente: undefined undefined

*/
```
El comportamiento del "**this**" en ==expresión de función flecha== es distinto al de ==expresión de función== cuando quiere referenciar al objeto.

  - El "**this**" queda ==atrapado dentro de la función flecha sin valor==.

<br>

Veámos de nuevo que ocurre si sacamos a la función fuera del objeto:
```js linenums="1"
const cliente = { 
    nombre: 'Roberto',
    apellido: 'Mendiburu'
};

const nombreCompleto = () => {
    console.log("this es: ", this); 
    console.log(`Cliente: ${this.nombre} ${this.apellido}`);
};


nombreCompleto(cliente);

/* Salida:

this es:  {}
Cliente: undefined undefined

*/
```
Ésta vez nos devuelve el mismo resultado.

  - El "**this**" vuelve a quedarse ==atrapado dentro de la función flecha sin valor==.

<br>

### Ejemplo 3
LLegado aquí, te preguntaras si es posible acceder a las propiedades del objeto desde fuera de ella utilizando "**this**". La respuesta es que si, ==hay un método para las funciones que se llama (función de enlace) "**bind()**" que permite enlazar el "**this**" con el objeto mediante argumento==.

### :material-code-braces: ==1 Objeto== + ==función de expresión==  + =="this"== + ==bind()==:
```js linenums="1"
const cliente = {
    nombre: 'Roberto',
    apellido: 'Mendiburu'
};

const nombreCompleto = function() {
    alert(`Cliente: ${this.nombre} ${this.apellido}`);
};

const enlaceCliente = nombreCompleto.bind(cliente);

enlaceCliente(); // Cliente: Roberto Mendiburu
```
<br>

### :material-code-braces: ==2 Objetos== + ==función de expresión==  + =="this"== + ==bind()==:
```js linenums="1"
const cliente_1 = {
    nombre: 'Roberto',
    apellido: 'Mendiburu'
};

const cliente_2 = {
    nombre: 'Julen',
    apellido: 'Mendoza'
};

const nombreCompleto = function() {
    alert(`Cliente: ${this.nombre} ${this.apellido}`);
};

const enlaceCliente_1 = nombreCompleto.bind(cliente_1);
const enlaceCliente_2 = nombreCompleto.bind(cliente_2);

enlaceCliente_1(); // Cliente: Roberto Mendiburu
enlaceCliente_2(); // Cliente: Julen Mendoza
```
<br>

Veámos que ocurre con la ==función flecha==: 
```js linenums="1"
const cliente = {
    nombre: 'Roberto',
    apellido: 'Mendiburu'
};

const nombreCompleto = () => {
    alert(`Cliente: ${this.nombre} ${this.apellido}`);
};

const enlaceCliente = nombreCompleto.bind(cliente);

enlaceCliente(); // Cliente: undefined undefined
```
Cabe recordar, que el "**this**" tampoco funciona con el método "**bind()**" en **función flecha**.

  - El "**this**" queda ==atrapado dentro de la función flecha sin valor==.

La única manera de enlazar el "**this**" con el objeto desde fuera de ella es con el uso de ==**función de expresión**== + =="**bind()**"==. Así es como trabaja el método (función de enlace).
***
<br>

#### Editor de código utilizado:

  - [Programiz - JavaScript Online Compiler :octicons-link-external-24:](https://www.programiz.com/javascript/online-compiler/){:target="_blank"}
<br>
<br>
