---
hide:
  #- navigation
  #- toc
---

# 3. ¿Cuáles son las tres funciones de String en JS?
JavaScript ofrece numerosas funciones predefinidas que facilitan el trabajo con cadenas de texto (==string==). Entre las posibilidades que ofrecen estas funciones tenemos el `replace()`, `toLowerCase()`, `toUpperCase()`, etc.

### ==replace()==:
El método ==.replace== acepta dos argumentos: la cadena que se reemplazará y con qué se reemplazará la cadena. Las cadenas en JavaScript son inmutables, el método `replace()` no cambia el valor de la cadena especificada, ==nos devuelve un nuevo valor==.

```js title="ejemplo.js"
let nombre = 'Roberto@gmail.com';

let resultado = nombre.replace('@gmail.com', '');

console.log(resultado); // Salida: Roberto
console.log(nombre); // Salida: Roberto@gmail.com
```

### ==toLowerCase()==:
Las cadenas en JavaScript son inmutables, el método `toLowerCase()` no cambia el valor de la cadena especificada, ==nos devuelve un nuevo valor==.

```js title="ejemplo.js"
let nombre = 'Roberto';

let resultado = nombre.toLowerCase();

console.log(resultado); // Salida: roberto
console.log(nombre); // Salida: Roberto
```

### ==toUpperCase()==:
Las cadenas en JavaScript son inmutables, el método `toUpperCase()` no cambia el valor de la cadena especificada, ==nos devuelve un nuevo valor==.

```js title="ejemplo.js"
let nombre = 'Roberto';

let resultado = nombre.toUpperCase();

console.log(resultado); // Salida: ROBERTO
console.log(nombre); // Salida: Roberto
```
<br>
<br>
