---
hide:
  #- navigation
  - toc
---

# 5. ¿Qué es un operador ternario?
==El operador ternario es una forma abreviada de la estructura **if**...**else**== y es útil cuando queremos tomar decisiones basadas en una condición.

**Se compone de tres partes:**

  - Una expresión condicional
  - Una expresión que se evalúa si la condición es verdadera
  - Una expresión que se evalúa si la condición es falsa

**La sintaxis básica del operador ternario es la siguiente:**

```js title="ejemplo.js"
condicion ? expresion_verdadera : expresion_falsa
```

!!! quote ""
    - **condicion**: Una expresión que se evalúa como verdadera o falsa
    - **expresion_verdadera**: La expresión que se ejecutará si condicion es verdadera
    - **expresion_falsa**: La expresión que se ejecutará si condicion es falsa

```js title="ejemplo.js"
const edad = 36;

const mensaje = edad >= 18 ? 'Eres mayor de edad' : 'Eres menor de edad';

console.log(mensaje); // Salida: Eres mayor de edad
```

### 5.1. Anidamiento de operadores ternarios
Es posible anidar operadores ternarios para expresiones condicionales más complejas. Los operadores ternarios encadenados (o anidados) hacen que el código sea imposible de leer en algunos casos. ==Lo ideal seria usar **switch/case** o **if/else** en su lugar==.

**Veamos un ejemplo**:

```js title="ejemplo.js"
const calificacion = 8;

const resultado = calificacion <   5 ? 'Suspenso' :
                  calificacion <   7 ? 'Aprobado' :
                  calificacion <   9 ? 'Notable' :
                  calificacion <  10 ? 'sobresaliente' :
                  calificacion == 10 ? 'Matrícula de honor' :
                                       'Introduzca un número del 0 al 10';

console.log(resultado); // Salida: Notable
```

!!! info "IMPORTANTE"
    Es importante mantener la legibilidad del código al hacerlo.
<br>
<br>
