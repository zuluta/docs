---
hide:
  #- navigation
  - toc
---
# <p style="color:#308830;">**2. ¿Cuáles son algunos tipos de datos JS?**</p>
Los tipos de datos en JavaScript son atributos que determinan el tipo de valor que puede contener una variable. Estos tipos de datos son utilizados para representar diferentes tipos de información.

JavaScript es un lenguaje de programación de ==tipado dinámico==, lo que significa que no es necesario declarar explícitamente el tipo de una variable al momento de su creación. Pero eso no significa que JavaScript no tenga tipos. Simplemente ==el tipo se determina automáticamente cuando se asigna un valor==.
<br>

### 2.1. Tipos de datos primitivos
Los tipos de datos primitivos son aquellos que representan valores individuales y no tienen métodos o propiedades. Son inmutables, lo que significa que no se pueden cambiar una vez que se han creado.

  - Cadena de texto (==string==)
  - Números (==number==)
  - Booleano (==boolean==)
  - Valor ==null==
  - Valor ==undefined==
<br>

### ==string==:
El tipo de datos `string` representa una secuencia de caracteres, como texto o palabras. Las cadenas se deben encerrar entre comillas simples `' '` o dobles `" "`.

```js
let nombre = 'Roberto';
let mensaje = "¡Hola mundo!";
```

### ==number==:
El tipo de datos `number` en JavaScript representa tanto números enteros como de punto flotante.

```js
let edad = 36;
let precio = 99.95;
```

### ==boolean==:
El tipo de datos `boolean` representa un valor de verdad, que puede ser `true` (verdadero) o `false` (falso). Es útil en expresiones condicionales y lógicas.

```js
let esHombre = true;
let esMujer = false;
```

### ==null==:
En JavaScript, `null` es un valor especial que representa la ausencia intencional de cualquier objeto o valor.

```js
let Unidades = null;
```

### ==undefined==:
El valor `undefined` indica que una variable ha sido declarada pero aún no se le ha asignado ningún valor.

```js
let unidades;
console.log(unidades); // Salida: undefined
```
<br>

### 2.2. Tipos de datos compuestos
Los tipos de datos compuestos en JavaScript son aquellos que pueden contener múltiples valores y tienen métodos y propiedades. Son mutables, lo que significa que pueden cambiar después de su creación.

  - Arrays (==array==)
  - Objetos (==object==)
<br>

### ==array==:
Los arrays en JavaScript son objetos especiales que permiten almacenar múltiples valores en una sola variable, indexados numéricamente.

```js
let animales = ['perro', 'oveja', 'caballo'];
```

### ==object==:
Los objetos en JavaScript son colecciones de pares clave-valor, donde la clave es una cadena (o símbolo) y el valor puede ser cualquier tipo de dato, incluidos otros objetos.

```js
let persona = {
    nombre: 'Roberto',
    edad: 36,
    casado: true
};
```
<br>
<br>
