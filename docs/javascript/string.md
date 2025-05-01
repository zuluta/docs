---
hide:
  #- navigation
  - toc
---

<link rel="stylesheet" href="../../assets/stylesheets/javascript.css">

# **Strings: Cadena de Caracteres**

En el mundo de la programación las cadenas de caracteres o strings son una de las estructuras de datos más utilizadas. Estas representan texto y permiten manipular datos textuales de manera flexible. En JavaScript, los strings son valores primitivos que se pueden utilizar para manejar y procesar texto en aplicaciones web.

En este artículo exploraremos cómo crear, manipular y utilizar strings en JavaScript, abarcando su uso común y buenas prácticas.

## **Creación de Strings en JavaScript**

Un string no es más que una colección de caracteres, como letras, números y símbolos y se puede crear utilizando comillas simples (`' '`), dobles (`" "`) o comillas invertidas (\`` `\`). Cada una tiene sus propios casos de uso:

  - **Comillas simples y dobles** se utilizan indistintamente para crear cadenas literales y se recomiendan cuando no se necesita interpolación.
  - **Comillas invertidas** (**template literals**), introducidas en ES6, permiten crear cadenas más dinámicas mediante la interpolación de variables y el soporte para cadenas multilínea.

**Ejemplos de Creación de Strings:**

```js linenums="1" title="javascript"
const saludo = "Hola, mundo";
const nombre = 'Juan Pérez';
const mensaje = `Bienvenido, ${nombre}!`;  // Template literal con interpolación
```

Las comillas invertidas son especialmente útiles cuando se necesita incluir variables dentro del string o definir cadenas con saltos de línea.

### **Constructor de Strings**

Además de crear cadenas utilizando la notación literal, JavaScript proporciona un constructor de objeto llamado `String()` que permite crear objetos de tipo cadena.

```js linenums="1" title="javascript"
const myString = new String('Hola mundo');

console.log(myString);
```

En el ejemplo anterior utilizamos el constructor `String()` para crear un nuevo objeto de cadena con el valor `"Hola mundo"`. Es importante tener en cuenta que aunque esto crea una cadena de caracteres, en la práctica es más común y preferible usar la notación literal de cadena debido a su simplicidad y claridad.

## **Longitud de un String**

Conocer la longitud de un string es importante para validar entradas de texto o para manipular los caracteres de manera precisa. En JavaScript, la propiedad `length` permite obtener el número de caracteres que componen una cadena.

```js linenums="1" title="javascript"
let mensaje = "Hola, JavaScript!";

console.log(mensaje.length);
```

En este caso `length` devuelve el número total de caracteres, incluidos los espacios y los signos de puntuación.

><br>
> Es importante tener en cuenta que en JavaScript existe el tipo String (con la primera letra en mayúscula), el cual es el tipo de contenedor primitivo para las cadenas. Esto significa que se pueden acceder a todas las propiedades y métodos del tipo String desde una cadena primitiva.
>
><br>

## **Acceso a los Caracteres de un String**

En JavaScript puedes acceder a los caracteres individuales de un string usando el índice, de manera similar a cómo accederías a los elementos de un array. Los índices comienzan en `0`, lo que significa que el primer carácter está en la posición `0`.

**Ejemplo de Acceso a Caracteres:**

```js linenums="1" title="javascript"
const texto = "JavaScript!!";

console.log(texto[0]);
console.log(texto[4]);
```

Este enfoque es útil cuando necesitas recorrer una cadena o extraer caracteres específicos.

Para acceder al último carácter de un string puedes utilizar el índice `length - 1`.

```js linenums="1" title="javascript"
const texto = "JavaScript!!";

console.log(texto[texto.length -1]);
```

Es importante recordar que las cadenas en JavaScript son **inmutables**, lo que significa que no puedes cambiar un carácter directamente usando esta notación.

## **Manipulación de Strings**

Aunque los strings en JavaScript son inmutables (no pueden ser modificados directamente), puedes crear nuevas cadenas a partir de las existentes. La manipulación de strings es esencial para formatear texto o combinar diferentes partes de una cadena.

### **1. Concatenación**

La concatenación se refiere a unir dos o más cadenas para formar una nueva. Puedes utilizar el operador `+` o `+=` para realizar la operación.

```js linenums="1" title="javascript"
const nombre = "Juan";
const apellido = "Pérez";
const nombreCompleto = nombre + " " + apellido;

console.log(nombreCompleto);
```

Este método es una forma sencilla y común de crear cadenas más complejas a partir de valores más simples.

### **2. Concatenación con Template Literals**

Los **template literals** ofrecen una forma más moderna y conveniente de concatenar strings. Al utilizar comillas invertidas (\`` `\`) puedes incluir variables directamente en el texto con la sintaxis `${variable}`.

```js linenums="1" title="javascript"
const producto = "Camisa";
const cantidad = 3;
const mensaje = `Tienes ${cantidad} ${producto}s en tu carrito.`;

console.log(mensaje);
```

Esta técnica no solo facilita la concatenación, sino que también permite el uso de saltos de línea y otros caracteres especiales sin necesidad de escape adicional.

## **Caracteres Especiales en Strings**

Los caracteres especiales son secuencias de escape que permiten incluir en el string elementos que no se pueden escribir directamente, como saltos de línea, comillas o caracteres Unicode.

**Ejemplos de Caracteres Especiales**

  - **Salto de línea** (`\n`): Inserta un salto de línea.
  - **Tabulación** (`\t`): Inserta un tabulador.
  - **Comillas**: Utiliza `'` o `"` para insertar comillas simples o dobles.

```js linenums="1" title="javascript"
const textoEspecial = "Primera línea\nSegunda línea";

console.log(textoEspecial); 
```

El uso de caracteres especiales es útil para formatear texto en mensajes de consola, archivos de texto y contenido HTML.

## **Convertir Otros Tipos de Datos a Strings**

En muchas situaciones es necesario convertir otros tipos de datos a cadenas. JavaScript ofrece varias formas de realizar esta conversión, lo cual es útil para mostrar valores numéricos, booleanos u otros datos como texto.

Puedes convertir a string utilizando `String()` o `.toString()`:

```js linenums="1" title="javascript"
const numero = 123;
const textoNumero = numero.toString();
console.log(textoNumero);

const booleano = true;
const textoBooleano = String(booleano);
console.log(textoBooleano);
```

Estas conversiones son esenciales para la manipulación de datos y la creación de mensajes dinámicos.

Tambien es importante destacar que el método `toString()` no funciona para valores `undefined` y `null`. Ademas, cuando se convierte una cadena a booleano, no se puede revertir el proceso.

## **Comparación de Strings**

Comparar cadenas de caracteres en JavaScript se hace utilizando operadores de comparación (`<`, `>`, `==`, `===`). La comparación de strings es sensible al orden lexicográfico (alfabético), donde el valor de cada carácter se basa en su código Unicode.

```js linenums="1" title="javascript"
const str1 = "apple";
const str2 = "banana";

console.log(str1 < str2);
```

En el ejemplo anterior `"apple"` es menor que `"banana"` porque la letra “a” tiene un código Unicode menor que la letra “b”.

Para comparaciones más específicas, como el ordenamiento en diferentes idiomas, puedes usar `localeCompare()`:

```js linenums="1" title="javascript"
const str1 = "apple";
const str2 = "banana";

console.log(str1.localeCompare(str2));
```

El método `localeCompare()` devuelve un número que indica si la cadena actual es menor, igual o mayor que la cadena comparada.

## **Otros Métodos Útiles**

Las cadenas de caracteres en JavaScript ofrecen una variedad de métodos integrados para su manipulación. Entre ellos se encuentran `split()`, `substring()`, `indexOf()`, `toUpperCase()`, `toLowerCase()`, entre otros. Estos métodos se exploran y detallan en tutoriales específicos.

***

### **Conclusión**

Las **cadenas de caracteres en JavaScript** son fundamentales para trabajar con datos textuales. Conocer las técnicas para crear, manipular y comparar strings te ayudará a manejar información textual de manera más efectiva en tus programas.

En el siguiente artículo exploraremos la diferencia entre [valores primitivos y valores de referencia en JavaScript](../valores-primitivos-vs-referencia/), cómo afectan la mutabilidad y el comportamiento de los datos en el lenguaje.

***

<br>
