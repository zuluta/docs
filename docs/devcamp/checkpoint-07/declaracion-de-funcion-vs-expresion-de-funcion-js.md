---
hide:
  #- navigation
  - toc
---

# <span style="color:#308830;">**6. ¿Cuál es la diferencia entre una declaración de función y una expresión de función?**</span>
JavaScript al ser un lenguaje dinámico, tiene ciertos mecanismos para garantizar que la ejecución de nuestro código sea la más óptima y correcta.

**Tenemos dos maneras principales de definir funciones:**

  - ==Podemos definir una función declarando== 
  - ==Podemos definir una función como una expresión==

**Veamos un ejemplo para compararlos:**

```js title="ejemplo.js"
// Declaracion de funcion
function saludar() {
    console.log('Hola');
}

// Expresion de funcion
let saludar = function() {
    console.log('Hola');
};
```

### 🕵️ Analicemos las diferencias

**Declaración de función:**

  - Sólo es visible dentro del bloque de código en el que reside, por ejemplo dentro de un `if`
  - JavaScript precarga todas las funciones declaradas al inicio y puede llamarse antes o despues de la función

**Expresión de función:**

  - Es visible dentro y fuera del bloque de código en el que reside pudiendo declarar una variable fuera del bloque
  - Se define dentro de una variable como una expresión normal, por eso lleva `;` punto y coma al final de la función
  - Solo puede llamarse despues de la función, si se llama antes de la función tira error de (variable no está definida)

!!! info ""
    Las diferencias de sintaxis son claras.

**Veamos el mismo ejemplo anterior, agregando una llamada antes de la función:**

```js title="ejemplo.js"
// Declaracion de funcion
saludar() // Salida: Hola

function saludar() {
    console.log('Hola');
}

// Expresion de funcion
saludar(); // Error: saludar no está definida

let saludar = function() {
    console.log('Hola');
};
```

En el caso de ==**expresión de función** nos da el error de (variable no está definida)==, cosa que en la declaración de función no ocurre gracias a la precarga de las declaraciones al inicio.

!!! info "IMPORTANTE"
    En las expresiones de funciones darle nombre a la función es opcional. En cambio para las declaraciones es obligatorio.

No hay una forma mejor o peor de declarar funciones, lo bueno es conocer las herramientas que tenemos, sus implicaciones y saber cuando podemos usarlas para crear código legible y limpio.

**Veamos un ejemplo mas completo:**

```js title="ejemplo.js"
// Expresion de funcion
let edad = 32;
let entradaCasino;

if (edad >= 18) {
    entradaCasino = function() {
        console.log('Puedes entrar al casino');
    };
}
else {
    entradaCasino = function() {
        console.log('No puedes entrar al casino');
    };
}

entradaCasino(); // Salida: Puedes entrar al casino
```

Con la **expresion de funcion**, podemos llamar a cualquier función este donde este. Gracias a la variable ==**entradaCasino**==, nos permite ver la función anónima dentro del bloque ==**if**== desde el exterior.
<br>
<br>
