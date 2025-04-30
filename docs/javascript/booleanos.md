---
hide:
  #- navigation
  - toc
---

<link rel="stylesheet" href="../../assets/stylesheets/javascript.css">

# **Booleanos**

En JavaScript, los booleanos son un tipo de dato fundamental que representa uno de dos valores: `true` o `false` (verdadero/falso). Este tipo se utiliza principalmente en estructuras de control, condiciones lógicas y bucles que determinan el flujo de ejecución de un programa.

En este artículo aprenderemos qué son los booleanos, cómo se utilizan y exploraremos algunos casos comunes para trabajarlos con condiciones y operadores lógicos.

## **¿Qué es un Booleano?**

Un booleano es un tipo de dato primitivo en JavaScript que representa un valor de verdad. Los únicos valores posibles son `true` (verdadero) o `false` (falso). En la programación se utilizan para evaluar expresiones y controlar el flujo del programa mediante decisiones basadas en condiciones.

```js linenums="1" title="javascript"
const esMayor = 10 > 5;
const esIgual = 10 === "10";

console.log(esMayor);
console.log(esIgual);
```

En el ejemplo anterior `esMayor` es `true` porque 10 es mayor que 5, mientras que `esIgual` es `false` debido a la no diferencia en el tipo de dato.

><br>
> Los valores literales del booleano distinguen entre mayúsculas y minúsculas. Esto significa que Truey False son identificadores válidos pero no son valores boolean.
>
><br>

Este tipo de datos denominado así en honor a George Boole, un matemático inglés conocido por su trabajo en lógica algebraica, se convirtió en una herramienta fundamental en las estructuras lógicas de los programas.

## **Valores Falsos y Verdaderos**

En JavaScript algunos valores se consideran “verdaderos” (truthy) y otros “falsos” (falsy) cuando se evalúan en un contexto booleano. Es importante conocer cuáles son estos valores para evitar errores al trabajar con condiciones.

### **Valores Falsy en JavaScript**

Los siguientes valores son considerados falsos en un contexto booleano:

  - `false`
  - `0`
  - `""` (cadena vacía)
  - `null`
  - `undefined`
  - `NaN` (Not a Number)

Cualquier otro valor se considera “verdadero” (truthy), lo que significa que se evalúa como `true`.

**Ejemplos de Valores Falsy y Truthy**

```js linenums="1" title="javascript"
if (0) {
    console.log("Esto no se ejecutará.");
}

if ("Hola") {
    console.log("Esto sí se ejecutará.");
}
```

En el ejemplo anterior `0` es un valor falsy y no activa el bloque `if`, mientras que la cadena `"Hola"` es truthy y activa el bloque.

## **Conversión de Valores Booleanos**

JavaScript permite convertir los valores de otros tipos a valores booleanos. Para convertir un valor no booleano en un valor booleano, utilizamos la función incorporada `Boolean()`

```js linenums="1" title="javascript"
const error = 'An error occurred';
const hasError = Boolean(error);

console.log(hasError);
```

En el ejemplo anterior declaramos una variable `error` que contiene el string ‘`An error occurred`‘. Luego utilizando la función `Boolean()`, convertimos el valor de la variable `error` a un booleano y lo almacenamos en la variable `hasError`. Al imprimir `hasError` en la consola, obtendremos `true` debido a que la variable `error` contiene un string no vacío, lo que hace que la función `Boolean()` lo evalúe como verdadero.

La siguiente tabla muestra cómo la función `Boolean()` convierte los valores de otros tipos en valores booleanos:

| Tipo de datos	  | Valores convertidos a verdaderos  | Valor convertido a falso |
| :-------------- | :-------------------------------- | :----------------------- |
| **`string`**	  | Cualquier cadena no vacía         | “” (string vacío)        |
| **`number`**	  | Cualquier número distinto de cero | 0, NaN                   |
| **`object`**	  | cualquier objeto	              | nulo                     |
| **`undefined`** | (Irrelevante)	                  | indefinido               |

**Ejemplos de Conversión a Booleano:**

```js linenums="1" title="javascript"
console.log(Boolean(1));
console.log(Boolean(0));
console.log(Boolean(""));
console.log(Boolean("Hola"));

// Uso del doble operador de negación
console.log(!!123);
console.log(!!"");
```

### **Coerción Implícita a Booleano**

En JavaScript se genera de manera implícita la **coerción de tipos a booleano**. Por ejemplo, la declaración `if` ejecuta un bloque si una condición es `true`. Si usa un valor no booleano usará la función `Boolean()` para convertir implícitamente ese valor a un valor booleano. Es decir, JavaScript convierte el valor a booleano automáticamente. Por ejemplo:

```js linenums="1" title="javascript"
const error = "An error occurred";

if (error) {
  console.log(error);
}
```

En cambio, si cambia el valor de la variable `error` a una cadena vacía (`""`), no imprimirá nada en la consola porque la declaración `if` lo evalúa como `false`:

## **Operadores Booleanos en JavaScript**

JavaScript cuenta con una variedad de operadores booleanos que permiten realizar operaciones lógicas y de comparación en el código. Estos operadores son esenciales para tomar decisiones basadas en condiciones y controlar el flujo del programa.

Hay seis tipos principales de operadores booleanos en JavaScript, cada uno con su función específica:


  1. AND lógico: Representado por `&&`.
  2. OR lógico: Representado por `||`.
  3. Comparación: Incluye operadores como `==`, `!=`, `<`, `>`, `<=` y `>=`.
  4. Comparación estricta: Representado por `===` y `!==`.
  5. NOT lógico: Representado por `!`.
  6. Operadores lógicos bitwise: Incluye `&` para AND, `|` para OR, `^` para XOR, `~` para NOT y `<<`, `>>` y `>>>` para desplazamiento de bits.

Mas adelante profundizamos en cada uno de los [operadores](../operadores-logicos/).

***

### **Conclusión**

Los **booleanos en JavaScript** son esenciales para la toma de decisiones y el control del flujo de los programas. Conocer los operadores lógicos, los valores truthy y falsy y cómo utilizar los booleanos en condiciones te permitirá escribir código más robusto y eficiente.

En el siguiente artículo profundizaremos en el uso de las [cadenas de caracteres (strings) en JavaScript](../string/), abordando sus métodos y aplicaciones comunes.

***

<br>
