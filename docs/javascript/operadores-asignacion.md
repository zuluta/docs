---
hide:
  #- navigation
  - toc
---

<link rel="stylesheet" href="../../assets/stylesheets/javascript.css">

# **Operadores de Asignación**

Los operadores de asignación en JavaScript son esenciales para almacenar y actualizar [valores en variables](../variables/). Además de la asignación básica (`=`), existen operadores compuestos que permiten realizar operaciones matemáticas y lógicas junto con la asignación en una sola línea de código.

En este artículo exploraremos los operadores de asignación estándar, sus características, ejemplos y recomendaciones para optimizar su uso.

## **¿Qué es un Operador de Asignación?**

Un operador de asignación es una entidad que toma el resultado de una expresión y lo almacena en una variable. El operador de asignación más básico en JavaScript es `=`, que asigna el valor de la derecha a la variable de la izquierda.

**Ejemplo de Asignación Básica:**

```js linenums="1" title="javascript"
const x = 10; // Se asigna el valor 10 a la constante x.
```

## **Operadores de Asignación Compuestos**

Los operadores de asignación compuestos en JavaScript realizan una operación matemática y asignan el resultado a una variable en un solo paso. Estos operadores son ideales para mejorar la legibilidad del código y optimizar operaciones repetitivas.

### **1. Suma Asignación (`+=`)**

El operador `+=` suma un valor a la variable existente y actualiza su valor. Es útil en operaciones como acumulación de totales o incrementos en contadores.

```js linenums="1" title="javascript"
let x = 5;
x += 3; // Equivalente a x = x + 3
```

**Ejemplo de uso básico**: Acumular un total en un bucle:

```js linenums="1" title="javascript"
let total = 0;
for (let i = 1; i <= 5; i++) {
  total += i; // Suma los valores del 1 al 5
}
console.log(total);
```

### **2. Resta Asignación (`-=`)**

El operador `-=` resta un valor de la variable y actualiza su valor. Es útil en casos como contadores decrecientes o ajustes acumulativos.

```js linenums="1" title="javascript"
let x = 10;
x -= 4; // Equivalente a x = x - 4
```

**Ejemplo de uso básico**: Reducir el saldo de un cliente tras una compra:

```js linenums="1" title="javascript"
let saldo = 100;
const gasto = 25;
saldo -= gasto; // Reduce el saldo por el gasto

console.log(saldo);
```

### **3. Multiplicación Asignación (`*=`)**

El operador `*=` multiplica el valor de la variable por el valor especificado y asigna el resultado.

```js linenums="1" title="javascript"
let x = 4;
x *= 2; // Equivalente a x = x * 2
```

**Ejemplo de uso básico**: Calcular el interés compuesto.

```js linenums="1" title="javascript"
let capital = 1000;
const tasa = 1.05; // 5% anual
capital *= tasa; // Primer año
capital *= tasa; // Segundo año

console.log(capital.toFixed(2));
```

### **4. División Asignación (`/=`)**

El operador `/=` divide el valor de la variable entre un divisor y actualiza su valor.

```js linenums="1" title="javascript"
let x = 20;
x /= 5; // Equivalente a x = x / 5
```

**Ejemplo de uso básico**: Repartir un monto entre varias personas.

```js linenums="1" title="javascript"
let monto = 100;
const personas = 4;
monto /= personas;

console.log(monto); // 25
```

### **5. Resto Asignación (`%=`)**

El operador `%=` divide el valor de la variable por el divisor y asigna el residuo resultante.

```js linenums="1" title="javascript"
let x = 10;
x %= 3; // Equivalente a x = x % 3
```

**Ejemplo de uso básico**: Determinar si un número es par o impar:

```js linenums="1" title="javascript"
let numero = 15;

console.log(numero % 2 === 0 ? "Par" : "Impar");
```

### **6. Exponenciación Asignación (`**=`)**

El operador `**=` eleva el valor de la variable a la potencia especificada y actualiza su valor.

```js linenums="1" title="javascript"
let x = 3;
x **= 2; // Equivalente a x = x ** 2
```

**Ejemplo de uso básico**: Calcular áreas o volúmenes:

```js linenums="1" title="javascript"
let radio = 3;
const exponente = 2; // Potencia cuadrada
let area = Math.PI;
area *= radio ** exponente; // Área de un círculo

console.log(area.toFixed(2));
```

En la siguiente tabla se resumen los operadores de asignación compuestos en JavaScript

| Operador	| Significado |	Descripción                                                                                                                 |
| :-------- | :---------- | :-------------------------------------------------------------------------------------------------------------------------- |
| a = b	    | a = b	      | Asigna el valor de `b` a `a`                                                                                                |
| a += b	| a = a + b	  | Suma el valor de `b` a `a` y asigna el resultado a `a`                                                                      |
| a -= b	| a = a - b	  | Resta el valor de `b` de `a` y asigna el resultado a `a`                                                                    |
| a *= b	| a = a * b	  | Multiplica `a` por el valor de `b` y asigna el resultado a `a`                                                              |
| a /= b	| a = a / b	  | Divide `a` por el valor de `b` y asigna el resultado a `a`                                                                  |
| a %= b	| a = a % b	  | Calcula el módulo de `a` con respecto a `b` y asigna el resultado a `a`                                                     |
| a &= b	| a = a & b	  | Realiza la operación AND entre `a` y `b` y asigna el resultado a `a`                                                        |
| a \|= b	| a = a \| b  | Realiza la operación OR entre `a` y `b` y asigna el resultado a `a`                                                         |
| a ^= b	| a = a ^ b	  | Realiza la operación XOR entre `a` y `b` y asigna el resultado a `a`                                                        |
| a <<= b	| a = a << b  | Realiza el desplazamiento de bits a la izquierda en `a` por `b` posiciones y asigna el resultado a `a`                      |
| a >>= b	| a = a >> b  | Realiza el desplazamiento de bits a la derecha (con signo conservado) en `a` por `b` posiciones y asigna el resultado a `a` |
| a >>>= b  | a = a >>> b | Realiza el desplazamiento de bits a la derecha (sin signo) en `a` por `b` posiciones y asigna el resultado a `a`            |

## **Encadenamiento de operadores de asignación**

JavaScript permite encadenar operadores de asignación para asignar el mismo valor a múltiples variables en una sola línea. Este encadenamiento evalúa la asignación de derecha a izquierda. Esto puede resultar útil para asignar un mismo valor a varias variables al mismo tiempo.

Por ejemplo, considera el siguiente código:

```js linenums="1" title="javascript"
let a = 10, b = 20, c = 30;
a = b = c; // Todas las variables ahora tienen el valor 30
```

JavaScript evalúa las asignaciones de derecha a izquierda. Por lo tanto, primero asigna el valor de `c` a `b`, y luego asigna el mismo valor de `b` a `a`. Como resultado, todas las variables `a`, `b` y `c` tienen el valor 30.

```js linenums="1" title="javascript"
let a, b, c;
a = b = c = 10;  // Asigna 10 a todas las variables

console.log(a, b, c);
```

En el anterior ejemplo asigna `10` a `c`, luego `b` toma el valor de `c`, y `a` toma el valor de `b`. Todas las variables terminan con el valor `10`.

Este tipo de encadenamiento de operadores de asignación puede ser útil cuando se trabaja con variables relacionadas que deben tener el mismo valor.

><br>
> El encadenamiento puede ser útil, pero es recomendable usarlo solo en situaciones simples para mantener la claridad del código.
>
><br>

## **Buenas Prácticas con Operadores de Asignación**

### **1. Usa Operadores Compuestos para Simplificar el Código**

Los operadores de asignación compuestos (`+=`, `-=`, `*=`, etc.) reducen el código y mejoran la legibilidad en operaciones repetitivas.

### **2. Encadenamiento para Asignaciones Simultáneas**

Si necesitas asignar el mismo valor a varias variables, el encadenamiento puede ser útil, pero evita su uso excesivo en casos complejos.

### **3. Familiarízate con la Prioridad de Operadores**

Recuerda que los operadores de asignación tienen una prioridad baja en el orden de evaluación. Esto significa que, en una expresión, otros operadores como `+`, `*`, etc., se evalúan primero. Usa paréntesis si necesitas alterar el orden de evaluación.

### **4. Evita Modificar Objetos Directamente con Operadores de Asignación**

En JavaScript, asignar un objeto a otro copia la referencia del objeto, no el valor. Para modificar una copia sin afectar el objeto original, usamos técnicas como [la desestructuración](../desestructuracion-de-objetos/) o el spread operator.

**Ejemplo Incorrecto:**

```js linenums="1" title="javascript"
const original = { nombre: "Juan" };
const copia = original;
copia.nombre = "Ana";

console.log(original.nombre);
```

**Ejemplo Correcto:**

```js linenums="1" title="javascript"
const original = { nombre: "Juan" };
const copia = { ...original };
copia.nombre = "Ana";

console.log(original.nombre);
```

***

### **Conclusión**

Los operadores de asignación en JavaScript facilitan la actualización de valores en variables de una manera eficiente y concisa. Al dominar los operadores de asignación compuestos y el encadenamiento, puedes escribir código más legible y eficiente. Además, aplicar buenas prácticas garantiza que los operadores se usen de forma clara y sin errores en el código.

En el próximo artículo, exploraremos los [Operadores Unarios en JavaScript](../operadores-unarios/), cubriendo los operadores `++`, `--`, y otros operadores específicos para trabajar con valores individuales.

***

<br>
