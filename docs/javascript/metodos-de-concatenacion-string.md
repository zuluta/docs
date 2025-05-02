---
hide:
  #- navigation
  - toc
---

<link rel="stylesheet" href="../../assets/stylesheets/javascript.css">

# **Métodos de Concatenación y Relleno en Strings**

En JavaScript, los métodos de concatenación y relleno no solo son herramientas útiles, sino que también ofrecen una solución directa para tareas como combinar [strings o cadenas de caracteres](../string/) dinámicamente, crear formatos visuales consistentes y construir patrones de texto repetitivos. Comprender cómo funcionan `concat`, `padStart`, `padEnd` y `repeat` te permitirá resolver problemas específicos de manipulación de strings con precisión y eficiencia.

## **Combina Strings de Forma Explícita: `concat`**

El método `concat` es una forma directa de unir dos o más cadenas en una sola. Aunque el operador `+` o los template literals (`${}`) suelen ser más populares, `concat` puede resultar útil cuando necesitas una función clara y explícita para manejar la combinación de strings.

```js linenums="1" title="javascript"
string1.concat(string2, string3, ..., stringN)
```

  - **`string1`**: String / Cadena base.
  - **`string2, ..., stringN`**: Strings o cadenas adicionales que deseas concatenar.

```js linenums="1" title="javascript"
const saludo = "Hola";
const nombre = "Mundo";
const mensaje = saludo.concat(", ", nombre, "!");

console.log(mensaje); // "Hola, Mundo!"
```

El método toma el string `"Hola"` y le añade `", "`, `"Mundo"`, y `"!"`, devolviendo una nueva cadena con todo concatenado.

El método `concat()` No modifica las cadenas originales, además devuelve una nueva cadena con los valores concatenados. Es más explícito que usar el operador `+`, aunque funcionalmente similar y permite concatenar múltiples cadenas en una sola llamada.

### **Ejemplo: Construir una URL con Concat()**

```js linenums="1" title="javascript"
const baseUrl = "https://www.ejemplo.com/";
const ruta = "articulo";
const id = "123";
const url = baseUrl.concat(ruta, "/", id);

console.log(url);
```

Normalmente se utiliza este método cuando se manejan múltiples variables dinámicas y quieres evitar el uso excesivo del operador `+`

```js linenums="1" title="javascript"
function crearMensaje(saludo, nombre) {
  return saludo.concat(", ", nombre, ".");
}

console.log(crearMensaje("Buenas tardes", "María"));
```

El método `concat()` es una forma explícita y legible de unir cadenas. Aunque no ofrece ventajas significativas sobre el operador `+`, es útil en casos donde la intención de concatenar debe ser clara.

## **Completar / Rellenar un String en su Inicio: `padStart`**

El método `padStart` es ideal para agregar caracteres al principio de un string, como ceros iniciales en números, espacios o cualquier otro símbolo necesario para alcanzar una longitud específica. Este método es comúnmente utilizado en formateos.

```js linenums="1" title="javascript"
string.padStart(targetLength, padString)
```

  - **`targetLength`**: La longitud deseada para la cadena resultante.
  - **`padString`** (opcional): La cadena con la que se rellenará. Por defecto es un espacio (`" "`).

Este método completa al inicio, es decir, rellena con el valor especificado al principio de la cadena, sin modificar la cadena o string original. A demás, si la longitud de la cadena es igual o mayor al parámetro recibido como `targetLength`, devuelve el string original.

**Ejemplo Básico:**

```js linenums="1" title="javascript"
const numero = "123";

console.log(numero.padStart(6, "0")); // "000123"
console.log(numero.padStart(8, "*")); // "*****123"
```

En el ejemplo anterior en el primer ejemplo, el string `"123"` se rellena con ceros al principio hasta alcanzar una longitud total de 6 caracteres. En el segundo ejemplo, se rellenan con asteriscos hasta alcanzar 8 caracteres.

El metodo `padStart` es ideal para formatear números o códigos con una longitud fija, como en identificadores o números de tarjeta:

```js linenums="1" title="javascript"
function formatearCodigo(codigo) {
  return codigo.toString().padStart(10, "0");
}

console.log(formatearCodigo(12345));
```

## **Completar / Rellenar un String en su final: `padEnd`**

Al contrario de `padStart`, `padEnd` agrega caracteres al final de una cadena de caracteres. Es especialmente útil para alinear texto o formatear columnas, como en tablas.

```js linenums="1" title="javascript"
string.padEnd(targetLength, padString)
```

  - **`targetLength`**: La longitud deseada de la cadena resultante.
  - **`padString`** (opcional): La cadena usada para rellenar. Por defecto es un espacio (`" "`).

El método `padEnd()` Completa al final, es decir rellena con el valor especificado al final del string. Este método No modifica la cadena original y si la longitud de la cadena es igual o mayor a `targetLength`, devuelve la cadena original.

```js linenums="1" title="javascript"
const texto = "Hola";

console.log(texto.padEnd(10, "."));
console.log(texto.padEnd(8, "!"));
```

En el código anterior el string `"Hola"` se extiende añadiendo puntos hasta que su longitud sea 10. En el segundo caso, se rellenan signos de exclamación hasta alcanzar 8 caracteres.

Este método es usado para formatear listas de texto con alineación visual, por ejemplo:

```js linenums="1" title="javascript"
function formatearColumna(titulo, dato) {
  return titulo.padEnd(15, " ") + dato;
}

console.log(formatearColumna("Nombre", "Juan"));
console.log(formatearColumna("Edad", "30"));
```

## **Genera Patrones Repitiendo un String: `repeat`**

El método `repeat` permite generar patrones de texto al repetir un string un número específico de veces. Es útil en tareas como la creación de separadores o cuando necesitas cadenas repetitivas.

```js linenums="1" title="javascript"
string.repeat(count)
```

  - **`count`**: Un número entero que indica cuántas veces se repetirá la cadena. Debe ser un valor positivo o cero, si es un decimal, se redondea hacia abajo.

```js linenums="1" title="javascript"
const texto = "¡Hola! ";

console.log(texto.repeat(3));
```

En el ejemplo anterior el string `"¡Hola! "` se repite tres veces y se concatena en una nueva cadena.

El método Crea una nueva cadena, repite la cadena original sin modificarla y Devuelve una cadena vacía si `count` es 0. También puede lanzar un error si `count` es negativo o infinito.

**Ejemplo: líneas decorativas** Un uso práctico es la creación de separadores o encabezados decorativos.

```js linenums="1" title="javascript"
const decoracion = "*".repeat(10);

console.log(decoracion); // "**********"
```

Crear patrones dinámicos:

```js linenums="1" title="javascript"
const filas = 5;
for (let i = 1; i <= filas; i++) {
    console.log("#".repeat(i));
}
```

Otro caso común es generar contenido estructurado, como cajas visuales:

```js linenums="1" title="javascript"
function crearCaja(texto, ancho) {
  const borde = "*".repeat(ancho);
  return `${borde}\n${texto.padStart((ancho + texto.length) / 2).padEnd(ancho)}\n${borde}`;
}

console.log(crearCaja("JavaScript", 20));
```

El método `repeat()` es perfecto para generar patrones repetitivos, líneas decorativas o replicar cadenas en bucles. Es una herramienta simple pero poderosa para tareas de diseño y manipulación de texto.

## **Formas de Utilizar los Métodos de Concatenación y Relleno**

  1. **Usa `concat` para una Semántica Clara**: Aunque los operadores `+` y `${}` son más comunes, `concat` puede ser útil cuando necesitas enfatizar que estás trabajando únicamente con strings.
  2. **`padStart` y `padEnd` en Formateo de Datos**: Estos métodos son perfectos para formatear contenido en interfaces de usuario, como reportes o sistemas de facturación.
  3. **Combina Métodos para Crear Estructuras Visuales**: Combinar `repeat`, `padStart` y `padEnd` puede ayudarte a generar contenido visualmente atractivo. Por ejemplo, puedes crear cuadros, tablas o patrones decorativos para interfaces de terminal o logs.
  4. **Optimiza el Uso de `repeat`**: Para tareas repetitivas, como generar separadores o encabezados, `repeat` es más eficiente y legible que concatenar manualmente un string varias veces.
  5. **Controla Longitudes Dinámicas con `padStart` y `padEnd`**: Úsalos para trabajar con cadenas de longitudes variables y asegurarte de que el resultado sea uniforme.
  6. **Ten en Cuenta el Rendimiento**: Aunque estos métodos son eficientes para tareas específicas, evita su uso excesivo en operaciones que procesen grandes cantidades de datos en ciclos.

***

### **Conclusión**

Los métodos de concatenación y relleno de JavaScript son herramientas extremadamente versátiles, ideales para combinar, extender o manipular strings en una amplia variedad de contextos. Su utilidad se extiende desde tareas simples, como agregar ceros iniciales en un número, hasta casos más avanzados, como crear estructuras visuales dinámicas.

***

<br>
