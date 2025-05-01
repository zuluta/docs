---
hide:
  #- navigation
  - toc
---

<link rel="stylesheet" href="../../assets/stylesheets/javascript.css">

# **Operadores Unarios**

En JavaScript, los operadores unarios son herramientas que permiten realizar transformaciones y manipulaciones sobre valores individuales con una sola instrucción. Desde convertir cadenas numéricas en números hasta optimizar cálculos incrementales o decrecientes, estos operadores son esenciales para resolver tareas comunes de forma elegante y eficiente.

Los operadores unarios de conversión, incremento y decremento nos permiten manipular valores numéricos de manera rápida y eficiente. En este tutorial exploraremos cómo funcionan y cómo utilizarlos en diferentes contextos.

## **Introducción a los Operadores Unarios**

Los operadores unarios son aquellos que trabajan con un solo valor. La siguiente lista detalla los operadores unarios y sus funciones:

  - **Unario Mas** `+x` : Convierte un valor en número
  - **Menos Unario** `-x` : Convierte un valor en número y lo niega
  - **Incremento** (**Prefijo**) `++x` : Añade uno al valor antes de su uso
  - **Decremento** (**Prefijo**) `--x` : Resta uno al valor antes de su uso
  - **Incremento** (**Postfijo**) `x++` : Añade uno al valor después de su uso
  - **Decremento** (**Postfijo**) `x--` : Resta uno al valor después de su uso

## **Conversión Numérica con Operadores Unarios**

Los operadores unarios `+` y `-` permiten convertir un valor en número, facilitando así las operaciones aritméticas en JavaScript, especialmente cuando se trata de strings que representan números.

### **1. Unario Más (`+x`)**

El operador unario `+` convierte un valor en número. Es útil cuando se quiere asegurar que una variable se trate como número, especialmente en el caso de strings numéricos. Para esto el interprete utiliza la función `Number()` siguiendo las siguientes reglas:

  - **Para valores booleanos**, false se convierte en 0 y true en 1.
  - **Para strings o cadenas**, se aplica una conversión de acuerdo con un conjunto específico de reglas.
  - **Para objetos**, se llama al método `valueOf()` y/o `toString()` para obtener el valor a convertir.

```js linenums="1" title="javascript"
const a = "5";

console.log(+a); // (convertido a número)
console.log(typeof +a);
```

Tener en cuenta que si el valor no es un número ni un string numérico, el resultado será `NaN` (Not-a-Number).

Ejemplo de Conversión con `+`: Este operador es ideal en casos donde se reciben datos en formato de texto que deben tratarse como números:

```js linenums="1" title="javascript"
const stringNumerico = "42";
const suma = +stringNumerico + 8;  // Convierte "42" a 42 y suma 8

console.log(suma); 
```

### **2. Unario Menos (`-x`)**

El operador `-` convierte un valor en número y lo niega. Esto es útil para transformar un string numérico en su equivalente negativo o para invertir el valor numérico de una variable.

```js linenums="1" title="javascript"
const b = "10";

console.log(-b);
```

### **Ejemplo de Conversión con `-`**

```js linenums="1" title="javascript"
const numTexto = "8";
const resultado = -numTexto;  // Convierte "8" a -8

console.log(resultado);
```

Este operador también devuelve `NaN` si el valor no se puede convertir a número.

## **Operadores de Incremento y Decremento**

Los operadores de incremento (`++`) y decremento (`--`) aumentan o disminuyen el valor de una variable en `1`. En JavaScript se pueden utilizar en dos formas: prefijo y postfijo y el orden en que se aplica afecta el resultado.

### **1. Incremento (`++`)**

El operador `++` incrementa el valor de una variable en `1`. Existen dos maneras de usarlo: prefijo (`++x`) y postfijo (`x++`).

**Prefijo** (`++x`): Cuando `++` se usa antes de la variable incrementa su valor inmediatamente y luego devuelve el valor incrementado. Esto es útil en casos donde el valor actualizado es necesario para la operación.

```js linenums="1" title="javascript"
let x = 5;

console.log(++x);  // incrementa antes de usar
console.log(x);
```

**Postfijo** (`x++`): Cuando `++` se usa después de la variable devuelve el valor actual y luego lo incrementa. Esto permite utilizar el valor original en una expresión antes de actualizarlo.

```js linenums="1" title="javascript"
let y = 5;

console.log(y++); // usa primero, incrementa después
console.log(y);
```

><br>
> El prefijo es preferible cuando se necesita el valor actualizado de inmediato, mientras que el postfijo es útil cuando se desea mantener el valor original temporalmente.
>
><br>

### **2. Decremento (`--`)**

El operador `--` funciona de manera similar a `++`, pero disminuye el valor de la variable en `1`.

**Prefijo** (`--x`): Cuando `--` se usa antes de la variable, decrementa el valor inmediatamente y luego devuelve el valor decrementado.

```js linenums="1" title="javascript"
let z = 3;

console.log(--z);
console.log(z);
```

**Postfijo** (`x--`): Cuando `--` se usa después de la variable, devuelve el valor actual y luego lo decrementa.

```js linenums="1" title="javascript"
let w = 3;

console.log(w--);  // usa primero, decrementa después
console.log(w);    //
```

><br>
> Como con ++, usa el prefijo para tener el valor actualizado de inmediato y el postfijo cuando necesitas el valor original primero.
>
><br>

## **Aplicaciones y Buenas Prácticas**

Los operadores `+` y `-` son una forma rápida y compacta de convertir strings a números en lugar de usar las funciones clasicas `Number()` o `parseInt()`.

**Ejemplo de Conversión:**

```js linenums="1" title="javascript"
const valorTexto = "100";
const resultado = +valorTexto * 2;  // Convierte a número y multiplica

console.log(resultado);
```

### **Seleccionar Entre Prefijo y Postfijo con Incremento/Decremento**

Elige prefijo o postfijo en función de cuándo necesitas el valor actualizado. Por ejemplo, en ciclos `for`, el postfijo `i++` es común porque se evalúa la condición primero y se incrementa después.

```js linenums="1" title="javascript"
let = 10
for (let i = 0; i < 5; i++) {
  console.log(i);
}
```

***

### **Conclusión**

Los operadores unarios de conversión, incremento y decremento en JavaScript son fundamentales para manipular valores de manera eficiente. Con `+` y `-`, puedes convertir strings a números de forma rápida. Los operadores `++` y `--` permiten incrementar y decrementar valores de acuerdo a la necesidad de cada contexto, ya sea en prefijo o postfijo.

En el próximo artículo, exploraremos los [Operadores de Comparación en JavaScript](../operadores-comparacion/), ideales para tomar decisiones y establecer condiciones en tu programa.

***

<br>
