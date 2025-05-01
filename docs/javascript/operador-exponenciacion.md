---
hide:
  #- navigation
  - toc
---

<link rel="stylesheet" href="../../assets/stylesheets/javascript.css">

# **Operador de Exponenciación**

Introducido en ES6, el operador de exponenciación (`**`) en JavaScript permite elevar un número a la potencia de otro, simplificando cálculos de potencias que antes se realizaban con `Math.pow`. Este operador es intuitivo y esencial para realizar operaciones matemáticas avanzadas. En este artículo exploraremos cómo funciona, sus aplicaciones y algunos detalles importantes para dominarlo.

## **¿Qué es el Operador de Exponenciación?**

El operador de exponenciación (`**`) en JavaScript eleva un número base a una potencia específica. Este operador es ampliamente utilizado en aplicaciones matemáticas y científicas. La sintaxis es:

```js linenums="1" title="javascript"
resultado = base ** exponente;
```

  - **`base`**: El número que deseas elevar.
  - **`exponente`**: La potencia a la que se eleva la base.

**Ejemplo Básico de Exponenciación:**

```js linenums="1" title="javascript"
const base = 2;
const exponente = 3;
const resultado = base ** exponente;

console.log(resultado);
```

En el anterior código vemos como `2 ** 3` representa `2`^`3`^, que equivale a `8`.

## **Comparación con `Math.pow()`**

Antes de ES6 la forma de calcular una potencia era usando `Math.pow`. Aunque la función aún sigue siendo válida, el operador `**` ofrece una sintaxis más breve y clara.

```js linenums="1" title="javascript"
const base = 4;
const exponente = 2;

console.log(Math.pow(base, exponente));
console.log(base ** exponente);
```

Ambas formas generan el mismo resultado, pero `**` suele preferirse por su simplicidad y legibilidad.

><br>
> Tenga en cuenta que algunos lenguajes utilizan el símbolo de intercalación ^ para la exponenciación. Sin embargo, JavaScript ya usa ese símbolo para el operador XOR lógico bit a bit.
>
><br>

Este operador eleva el número de la base al exponente especificado. Además, el operador de exponenciación acepta tanto valores `number` como `bigint`.

## **Exponenciación con Números Negativos**

El operador de exponenciación en JavaScript permite tanto bases como exponentes negativos, pero existen algunas consideraciones importantes sobre cómo se comporta con estos valores. Veamos:

### **Bases Negativas:**

Cuando la base es negativa el resultado depende de si el exponente es par o impar. Si el exponente es par, el resultado será positivo; si es impar, el resultado será negativo.

```js linenums="1" title="javascript"
const base = -2;
const exponentePar = 4;
const exponenteImpar = 3;

console.log(base ** exponentePar);  // (par)
console.log(base ** exponenteImpar); // (impar)
```

En el código anterior vemos que la primera salida en consola es un numero par `(-2) ** 4` da `16`, ya que elevar un número negativo a una potencia par siempre resulta en un valor positivo. En la segunda salida da negativo porque `(-2) ** 3` da `-8`, ya que una potencia impar mantiene el signo negativo.

### **Exponentes Negativos:**

Cuando el exponente es negativo el operador devuelve el recíproco de la potencia. Esto equivale a dividir `1` entre el valor de la base elevada a la potencia positiva del exponente.

```js linenums="1" title="javascript"
const base = 5;
const exponenteNegativo = -2;

console.log(base ** exponenteNegativo);  // (equivalente a 1 / 25)
```

Aquí, `5 ** -2` es lo mismo que `1 / (5 ** 2)`, resultando en `0.04`.

## **Exponenciación y Conversiones Implícitas de Tipo**

Cuando uno de los operandos del operador de exponenciación es un string que representa un número, JavaScript intentará convertirlo automáticamente a un valor numérico antes de realizar la operación. Si la conversión falla, el resultado será `NaN`.

**Ejemplo de Conversión Implícita:**

```js linenums="1" title="javascript"
console.log("2" ** 3);  // (convierte "2" a número)
console.log(2 ** "3");  // (convierte "3" a número)
console.log("Hola" ** 2);  // (no se puede convertir)
```

JavaScript utiliza el método `Number()` para intentar convertir strings en valores numéricos y si el string no es convertible (como en `"Hola"`), el resultado es `NaN`.

## **Prioridad del Operador de Exponenciación**

El operador de exponenciación tiene una prioridad alta en JavaScript, incluso más alta que los operadores de multiplicación y división. Esto significa que cualquier operación de exponenciación se evaluará antes que multiplicaciones o divisiones, a menos que se utilicen paréntesis para controlar el orden de ejecución.

**Ejemplo de Prioridad:**

```js linenums="1" title="javascript"
const resultado = 2 * 3 ** 2;

console.log(resultado);
```

En este caso, `3 ** 2` se evalúa primero, y luego el resultado (`9`) se multiplica por `2`. Para alterar el orden de ejecución, se pueden usar paréntesis:

```js linenums="1" title="javascript"
let resultado = (2 * 3) ** 2;

console.log(resultado);
```

Aquí, `2 * 3` se evalúa primero, y el resultado (`6`) se eleva a `2`.

## **Consideraciones para Usar Exponenciación**

  - **Conoce el Comportamiento con Negativos**: Entiende cómo `**` afecta a bases y exponentes negativos, especialmente en cálculos donde el signo es importante.
  - **Aprovecha las Conversiones Implícitas**: Si los operandos son strings numéricos, JavaScript los convierte automáticamente, pero asegúrate de que los datos sean numéricos para evitar `NaN`.
  - **Usa Paréntesis para Controlar el Orden de Evaluación**: Debido a la alta prioridad de `**`, los paréntesis pueden ayudar a evitar cálculos inesperados.

***

### **Conclusión**

El operador de exponenciación (`**`) en JavaScript es una herramienta poderosa para elevar valores a una potencia, útil en aplicaciones matemáticas, científicas y financieras. Con su alta prioridad y su capacidad de manejar bases y exponentes negativos, este operador simplifica muchos cálculos que antes requerían `Math.pow`. Al comprender su funcionamiento y buenas prácticas, puedes aprovechar al máximo este operador en tus proyectos.

***

<br>
