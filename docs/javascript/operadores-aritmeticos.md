---
hide:
  #- navigation
  - toc
---

<link rel="stylesheet" href="../../assets/stylesheets/javascript.css">

# **Operadores Aritméticos**

Los operadores aritméticos en JavaScript permiten realizar cálculos matemáticos básicos u avanzados. Además de las operaciones básicas conocidas, estos operadores interactúan de diferentes formas con distintos tipos de datos, incluyendo conversiones automáticas y objetos.

Este artículo explora cada operador aritmético, sus características especiales y sus aplicaciones prácticas.

## **¿Qué son los Operadores Aritméticos?**

Los operadores aritméticos son símbolos que indican al intérprete la realizaciones de operaciones matemáticas entre valores. Aunque se usan principalmente para operaciones numéricas, también pueden interactúan con otros tipos de datos como por ejemplo, los strings u objetos, generando así conversiones automáticas o comportamientos especiales.

### **Tipos de Operadores Aritméticos en JavaScript**

JavaScript ofrece una serie de operadores aritméticos estándar que son fundamentales para realizar operaciones matemáticas. Estos son:

  - Suma (`+`)
  - Resta (`-`)
  - Multiplicación (`*`)
  - División (`/`)
  - Módulo o Resto (`%`)
  - Exponenciación (`**`)

## **Operador de Suma**

El operador de suma `+` permite la adicción de valores numéricos. Además, cuando uno de los operandos es un string, este operador actúa como operador de concatenación, uniendo el texto de ambos lados.

**Ejemplo de Suma y Concatenación:**

```js linenums="1" title="javascript"
const a = 10;
const b = 5;
console.log(a + b);

const saludo = "Hola, ";
const nombre = "JavaScript";
const mensaje = saludo + nombre;
console.log(mensaje);
```

**Uso con Números Negativos**: Si uno de los valores es negativo, la operación aritmética los suma o resta según corresponda.

```js linenums="1" title="javascript"
const x = -7;
const y = 3;
console.log(x + y);
```

### **Conversión Implícita con el Operador `+`**

JavaScript realiza conversiones automáticas en ciertos casos. Cuando `+` combina un número con un string, convierte automáticamente el número a texto para concatenarlo en lugar de realizar una suma.

```js linenums="1" title="javascript"
const numero = 5; // tipo numbre
const texto = " es un número"; // tipo string

console.log(numero + texto);
```

Esto ocurre porque el operador `+` tiene una doble función: suma y concatenación. Si uno de los operandos es un string, el interprete de JavaScript considera que el contexto es textual y convierte el número en string.

## **Operador de Resta**

El operador de resta (`-`) en JavaScript calcula la diferencia entre dos valores numéricos. También se utiliza para operar con valores negativos siguiendo las reglas matemáticas estándar.

```js linenums="1" title="javascript"
const a = 10;
const b = 5;
const result = a - b;

console.log(result);
```

**Resta de variables con valores negativos:**

La resta de variables con valores negativos en JavaScript sigue las mismas reglas matemáticas que la resta de números positivos. Cuando restas un número negativo de otro número, estás sumando el valor absoluto del número negativo al primer número.

```js linenums="1" title="javascript"
const numero1 = -10;
const numero2 = -5;

console.log(numero1 - numero2);
```

### **Conversión Implícita en Resta**

A diferencia de la suma, el operador de resta (`-`) no tiene un rol secundario como concatenación de strings. Esto significa que si uno de los operandos es un string que contiene un número, el interprete intentará convertirlo a un número mediante coerción implícita para poder realizar la operación. Este proceso se basa en el método `Number()`, el cual intenta transformar el string a un número. Si la conversión falla, el resultado será `NaN`.

```js linenums="1" title="javascript"
const x = "10";
const y = 5;

console.log(x - y);  // (convierte "10" a 10)
```

Este proceso evita errores y permite restas con datos que puedan estar almacenados como texto numérico.

## **Operador de Multiplicación**

El operador de multiplicación (`*`) en JavaScript multiplica dos valores y devuelve su producto. Si uno de los valores es negativo, el resultado también será negativo, básicamente sigue las reglas matemáticas estándar.

```js linenums="1" title="javascript"
const result = 2 * 3;

console.log(result);
```

### **Conversiones en Multiplicación**

Al igual que en la resta, si uno de los operandos es un string que contiene un número, el interprete de JavaScript intenta convertirlo a un valor numérico utilizando la función Number(). Este proceso de conversión implícita permite realizar la operación sin necesidad de una conversión manual, esto siempre y cuando el string represente un valor numérico válido.

```js linenums="1" title="javascript"
const x = "3";
const y = 4;

console.log(x * y);
```

Si el string no representa un número, el resultado será `NaN`, indicando que la conversión falló.

## **Operador de División**

El operador de división (`/`) en JavaScript divide un valor entre otro y devuelve el cociente. Si el divisor es `0`, el resultado será `Infinity` o `-Infinity`, dependiendo del signo del dividendo.

```js linenums="1" title="javascript"
const result = 20 / 10;

console.log(result);
```

### **División de Valores No Numéricos**

Cuando uno de los operandos es un string que representa un número, JavaScript utiliza la conversión implícita para transformar el string a un número si es posible. Si el valor no es numérico, el resultado es `NaN`.

```js linenums="1" title="javascript"
console.log("20" / 2);
console.log("Hola" / 2);
```

El interprete del lenguaje intenta convertir el string `“20”` a un número y logra hacer la división. Sin embargo, cuando el string no es convertible, como en `"Hola"`, el resultado es `NaN`.

## **Operadores Aritméticos con Objetos en JavaScript**

Cuando se aplican operadores aritméticos a objetos, JavaScript intenta convertirlos en valores primitivos mediante el método `valueOf()` o `toString()`. Si el objeto tiene un método `valueOf()` que devuelve un número, este se utiliza para la operación. Si `valueOf()` no existe o devuelve un valor no numérico, JavaScript intenta usar `toString()`.

**Ejemplo con Objetos Personalizados:**

```js linenums="1" title="javascript"
const objeto = {
  valueOf() {
    return 10;
  }
};

console.log(objeto + 5);
console.log(objeto * 2);
```

JavaScript invoca `valueOf()` para obtener un valor numérico del objeto, permitiendo que el operador realice la operación aritmética.

## **Precisión y Problemas con Decimales en JavaScript**

JavaScript utiliza el formato de punto flotante de doble precisión (IEEE 754) para representar números, lo que puede ocasionar errores de precisión al realizar operaciones con decimales. Estos errores se deben a que ciertos valores no pueden representarse exactamente en binario, lo que genera resultados inesperados.

```js linenums="1" title="javascript"
const x = 0.1;
const y = 0.2;

console.log(x + y);
```

En este caso, la suma de `0.1` y `0.2` no es exactamente `0.3` debido a las limitaciones del formato binario.

**Cómo solucionar estos problemas:**

  - **Redondeo de resultados**: Puedes redondear el resultado a un número fijo de decimales usando el `método` `toFixed()` o el constructor `Number`.
  - **Trabajar con enteros**: Otra técnica es evitar los decimales durante los cálculos multiplicando los números por una potencia de 10 antes de operar y dividiéndolos al final.

Si necesitas mayor precisión en operaciones complejas, considera utilizar librerías especializadas como [Big.js](https://mikemcl.github.io/big.js/) o Decimal.js, que manejan números decimales con exactitud.

## **Prioridad de los Operadores Aritméticos**

En JavaScript, los operadores aritméticos se evalúan siguiendo un orden de prioridad predefinido, lo que afecta cómo se ejecutan las operaciones en expresiones complejas. Este orden es:

  1. Exponenciación (`**`)
  2. Multiplicación (`*`), División (`/`) y Módulo (`%`)
  3. Suma (`+`) y Resta (`-`)

Los operadores con mayor prioridad se evalúan antes. Cuando los operadores tienen la misma prioridad, se ejecutan de izquierda a derecha, excepto la exponenciación (`**`), que se evalúa de derecha a izquierda.

```js linenums="1" title="javascript"
const resultado = 5 + 2 * 3 ** 2;

console.log(resultado);
```

**Explicación del ejemplo:**

  1. Finalmente, se suma: `5 + 18` → `23`.
  2. Primero, se evalúa la exponenciación: `3 ** 2` → `9`.
  3. Luego, se realiza la multiplicación: `2 * 9` → `18`.

Para cambiar el orden en el que se ejecutan las operaciones puedes usar paréntesis, que tienen la prioridad más alta. Esto también mejora la legibilidad del código:

```js linenums="1" title="javascript"
const resultado = (5 + 2) * (3 ** 2);

console.log(resultado);
```

**En este caso:**

  1. Primero se evalúan las expresiones dentro de los paréntesis: `5 + 2` → `7` y `3 ** 2` → `9`.
  2. Luego, se realiza la multiplicación: `7 * 9` → `63`.

***

## **Buenas Prácticas en el uso de Operadores Aritméticos**

  - **Usa Paréntesis para Claridad**: Aunque los operadores tienen prioridad, los paréntesis ayudan a que el código sea más legible.
  - **Controla Conversiones Implícitas**: Conoce cómo cada operador convierte valores al usarse con diferentes tipos de datos.
  - **Evita Errores de Precisión con Decimales**: Considera redondear o manejar decimales con métodos adicionales si se requiere precisión.

***

### **Conclusión**

Los operadores aritméticos en JavaScript ofrecen gran versatilidad para trabajar con números y datos en el código. Entender cómo operan con distintos tipos, como strings y objetos, así como los problemas de precisión con decimales, ayuda a escribir código preciso y funcional.

En el siguiente artículo profundizaremos en los [Operadores de Resto](../operador-resto/) que nos permite obtener el resto de una división entre dos números.

***

<br>
