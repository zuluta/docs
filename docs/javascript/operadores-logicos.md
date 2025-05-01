---
hide:
  #- navigation
  - toc
---

<link rel="stylesheet" href="../../assets/stylesheets/javascript.css">

# **Operadores lógicos**

Los operadores lógicos en JavaScript permiten combinar y evaluar condiciones, facilitando la toma de decisiones y el control del flujo de un programa. En este artículo, exploraremos los tres operadores lógicos principales: `&&` (AND), `||` (OR) y `!` (NOT), explicando cómo funcionan y cuándo usarlos en distintos contextos.

## **¿Qué son los Operadores Lógicos?**

Los operadores lógicos en JavaScript son entidades que se utilizan para evaluar expresiones booleanas, devolviendo `true` o `false` según las condiciones evaluadas. Estos operadores son fundamentales para construir lógica condicional en estructuras del lenguajes como [if](../declaracion-if-else/), [while](../bucle-while/), y [for](../bucle-for/).

***

## **Operador Lógico AND (&&)**

El operador `&&` (AND) evalúa dos expresiones y devuelve `true` solo si ambas son verdaderas. Si alguna de las expresiones es `false`, el operador `&&` devuelve `false`. Este operador evalúa de izquierda a derecha y usa un cortocircuito: Es decir, si la primera expresión es `false`, no evalúa la segunda.

**Sintaxis:**

```js linenums="1" title="javascript"
resultado = expr1 && expr2;
```

En el siguiente ejemplo ambas condiciones pasadas deben ser verdaderas para permitir la conducción.

```js linenums="1" title="javascript"
const edad = 25;
const tieneLicencia = true;

if (edad >= 18 && tieneLicencia) {
  console.log("Puedes conducir.");
} else {
  console.log("No puedes conducir.");
}
```

### **Cortocircuito con `&&`**

Cuando el operador `&&` encuentra una expresión `false` deja de evaluar las demás. Esto permite optimizar el código y evita ejecutar código innecesario.

```js linenums="1" title="javascript"
const resultado = false && (5 / 0);

console.log(resultado);
```

Utiliza `&&` para validar múltiples condiciones que deben cumplirse en su totalidad o para evitar que se ejecute código innecesario si una condición falla.

## **Operador Lógico OR (`||`)**

El operador lógico `||` (OR) evalúa dos expresiones y devuelve `true` si al menos una de ellas es verdadera. Si ambas expresiones son `false`, entonces `||` devuelve `false`.

Este operador también aplica cortocircuito: si la primera expresión es true, no evalúa la segunda.

**Sintaxis:**

```js linenums="1" title="javascript"
resultado = expr1 || expr2;
```

En el siguiente ejemplo: `usuario` es una cadena vacía (`""`) que se evalúa como `false`. Por lo tanto, `nombre` toma el valor de `nombrePredeterminado`.

```js linenums="1" title="javascript"
const usuario = "";
const nombrePredeterminado = "Invitado";

const nombre = usuario || nombrePredeterminado;
console.log(nombre);
```

### **Cortocircuito con `||`**

El operador `||` detiene la evaluación si encuentra un valor `true`, omitiendo el resto de las expresiones.

```js linenums="1" title="javascript"
const resultado = true || (5 / 0);

console.log(resultado);
```

**Tip de Uso**: `||` es ideal para establecer valores predeterminados o para verificar que al menos una condición sea verdadera.

## **Operador Lógico NOT (`!`)**

El operador `!` (NOT) invierte el valor booleano de una expresión. Si una expresión es `true`, el operador NOT la convierte en `false` y viceversa. Este operador es útil para validar condiciones opuestas o para comprobar si una variable no cumple con un valor esperado.

**Sintaxis:**

```js linenums="1" title="javascript"
resultado = !expr;
```

El siguiente ejemplo `!acceso` invierte el valor de `acceso` para verificar si es `false`.

```js linenums="1" title="javascript"
const acceso = false;

if (!acceso) {
  console.log("Acceso denegado.");
} else {
  console.log("Bienvenido.");
}
```

El operador lógico NOT funciona basándose en las siguientes reglas:

```js linenums="1" title="javascript"
!a
```

Según la expresión anterior:

  - Si `a` es así `undefined`, el resultado es `true`.
  - Si `a` es así `null`, el resultado es `true`.
  - Si `a` es un número distinto de `0`, el resultado es `false`.
  - Si `a` es así `NaN`, el resultado es `true`.
  - Si `a` es un objeto, el resultado es `false`.
  - Si `a` es un string vacío, el resultado es verdadero. En el caso `a` de que sea un string no vacío, el resultado es `false`

```js linenums="1" title="javascript"
console.log(!undefined);
console.log(!null);
console.log(!20);
console.log(!0);
console.log(!NaN);
console.log(!{});
console.log(!'');
console.log(!'OK');
console.log(!false);
console.log(!true);
```

### **Doble negación (`!!`)**

A veces es posible que veas la doble negación (`!!`) en el código. Este se utiliza para convertir un valor a su valor booleano real.

El doble NOT (`!!`) convierte cualquier valor a booleano, siendo una manera rápida de evaluar si una variable tiene un valor “verdadero” o “falso”.

```js linenums="1" title="javascript"
const nombre = "JavaScript";

console.log(!!nombre);  // (tiene un valor)
```

El resultado es el mismo que si se utilizara la función booleana() . Usa `!!` para convertir expresiones en booleanos sin necesidad de una declaración `if`.

## **Combinación de Operadores Lógicos**

JavaScript permite combinar operadores lógicos en una sola expresión, lo cual es útil para evaluar múltiples condiciones. La prioridad del operador lógico determina el orden en que se evalúan las expresiones lógicas en JavaScript. En general, el operador `&&` (Y lógico) tiene mayor prioridad que el operador `||` (O lógico). Esto significa que las expresiones con `&&` se evalúan antes que las expresiones con `||`.

En otras palabras, la precedencia de los operadores es el orden de evaluación de los operadores lógicos en una expresión.

**Ejemplo de Combinación:**

```js linenums="1" title="javascript"
const edad = 20;
const tieneLicencia = true;
const haTomadoCurso = false;

if ((edad >= 18 && tieneLicencia) || haTomadoCurso) {
  console.log("Puedes acceder al sistema.");
} else {
  console.log("No tienes acceso.");
}
```

En el ejemplo anterior:

  1. Primero se evalúa `(edad >= 18 && tieneLicencia)`, que es `true`.
  2. Luego se evalúa `true || haTomadoCurso`, que también es `true`, por lo que la condición se cumple.

Usa paréntesis para asegurarte de que las condiciones se evalúen en el orden correcto y mejorar la legibilidad del código.

## **Buenas Prácticas con Operadores Lógicos**

  1. **Usa `&&` y `||` para Asignar Valores Predeterminados**: Estos operadores pueden simplificar asignaciones de valores predeterminados y evitar el uso excesivo de `if`
  2. **Doble NOT (`!!`) para Evaluación Booleana**: El uso de `!!` es una forma rápida de convertir cualquier valor en booleano, útil para verificar si una variable tiene un valor asignado.
  3. **Evita Expresiones Demasiado Largas**: Al combinar múltiples operadores lógicos, usa paréntesis para mantener la claridad y garantizar el orden de evaluación deseado.
  4. **Aprovecha el Cortocircuito**: Usa el comportamiento de cortocircuito de `&&` y `||` para evitar la ejecución de operaciones innecesarias y optimizar el rendimiento.

***

### **Conclusión**

Los operadores lógicos en JavaScript son herramientas esenciales para evaluar múltiples condiciones y tomar decisiones complejas de forma sencilla. Al dominar `&&`, `||` y `!`, puedes escribir código más claro y eficiente, permitiendo controlar el flujo de tu programa de manera precisa.

En el próximo artículo exploraremos los [Operadores de Asignación en JavaScript](../operadores-asignacion-logica/) y cómo pueden ayudarte a asignar valores de manera más flexible y controlada.

***

<br>
