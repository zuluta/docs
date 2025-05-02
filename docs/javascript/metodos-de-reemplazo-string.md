---
hide:
  #- navigation
  - toc
---

<link rel="stylesheet" href="../../assets/stylesheets/javascript.css">

# **Métodos de Reemplazo en Strings**

Reemplazar texto en JavaScript es una operación común y poderosa que permite modificar strings para adaptarlas a diferentes necesidades. Los métodos de reemplazo: `replace` y `replaceAll` son herramientas que nos son útiles para estas tareas, nos ofrecen flexibilidad y eficiencia en la manipulación de cadenas de caracteres. A continuación exploraremos cómo funcionan, sus diferencias y casos de uso prácticos.

## **Reemplaza la Primera Ocurrencia de un Texto: `replace()`**

El método `replace` sustituye la primera coincidencia de una subcadena o un patrón en el string por otro texto especificado como parámetro en el método. Es una solución sencilla para modificaciones específicas.

```js linenums="1" title="javascript"
string.replace(pattern, replacement);
```

  - **`pattern`**: Puede ser un string o una expresión regular.
  - **`replacement`**: El texto que sustituirá la coincidencia.

El método **No modifica la cadena original** y este retorna una nueva cadena con los reemplazos aplicados. Solo reemplaza la **primera coincidencia** si el `pattern` es una cadena o una expresión regular sin el modificador global (`g`). Puede reemplazar usando un texto estático o el resultado de una función.

### **Reemplazo simple con cadenas**

```js linenums="1" title="javascript"
const texto = "JavaScript es divertido. Aprender JavaScript es útil.";
const resultado = texto.replace("JavaScript", "Python");

console.log(resultado); // "Python es divertido. Aprender JavaScript es útil."
```

Solo la primera aparición de `"JavaScript"` es reemplazada por `"Python"`. Las coincidencias posteriores no se ven afectadas.

### **Uso con Expresiones Regulares**

Cuando se utiliza una expresión regular como patrón, puedes realizar reemplazos más flexibles:

```js linenums="1" title="javascript"
const texto = "Aprender es divertido. Aprender JavaScript es útil.";
const resultado = texto.replace(/aprender/i, "Estudiar");

console.log(resultado); // "Estudiar es divertido. Aprender JavaScript es útil."
```

La bandera `i` permite que el patrón ignore mayúsculas y minúsculas, reemplazando `"Aprender"` por `"Estudiar"`.

### **Ejemplo: Reemplazar palabras clave en una descripción o comentario:**

```js linenums="1" title="javascript"
const comentario = "El producto es caro y el envío es caro.";
const actualizado = comentario.replace("caro", "costoso");

console.log(actualizado); // "El producto es costoso y el envío es caro."
```

### **Ventajas del método replace()**

  1. **Flexibilidad**: Soporta reemplazos estáticos y dinámicos.
  2. **Compatibilidad con expresiones regulares**: Lo hace poderoso para búsquedas y modificaciones avanzadas.
  3. **Manejo dinámico**: Usar funciones como reemplazo permite una lógica compleja.

## **Reemplaza Todas las Ocurrencias de un Texto: `replaceAll()`**

El método `replaceAll` es una versión extendida de `replace`, este fue diseñado específicamente para reemplazar todas las apariciones de un patrón o subcadena en un string.

```js linenums="1" title="javascript"
string.replaceAll(pattern, replacement);
```

  - **`pattern`**: Puede ser un string o una expresión regular con la bandera global (g).
  - **`replacement`**: El texto que sustituirá todas las coincidencias.

Este método reemplaza todas las coincidencias de forma directa (no solo la primera como `replace()`). Permite el uso de cadenas o expresiones regulares globales como patrón y No modifica la cadena original, sino que devuelve una nueva con los reemplazos aplicados.

Es más legible y directo para reemplazos múltiples que `replace()` combinado con expresiones regulares globales.

### **Reemplazo simple con cadenas**

```js linenums="1" title="javascript"
const text = "Hola mundo, mundo hermoso";
const newText = text.replaceAll("mundo", "JavaScript");

console.log(newText); // "Hola JavaScript, JavaScript hermoso"
```

### **Reemplazo con expresiones regulares globales**

Aunque `replaceAll` no requiere el modificador `g`, puedes usarlo con expresiones regulares.

```js linenums="1" title="javascript"
const text = "123-456-789";
const newText = text.replaceAll(/\d/g, "*");

console.log(newText); // "***-***-***"
```

### **Caso de Uso: Limpiar texto de caracteres no deseados:**

```js linenums="1" title="javascript"
const texto = "123-456-7890";
const limpio = texto.replaceAll("-", "");

console.log(limpio); // "1234567890"

```

Esto es útil en escenarios donde necesitas estandarizar números o datos formateados.

## **Diferencias Clave entre replace y replaceAll**

  1. **Cantidad de Reemplazos**:
    - `replace` solo reemplaza la **primera** coincidencia.
    - `replaceAll` reemplaza **todas** las coincidencias.
  2. **Compatibilidad**:
    - `replace` es ampliamente compatible con todas las versiones modernas de JavaScript.
    - `replaceAll` fue introducido en **ES2021**, por lo que podría no estar disponible en entornos más antiguos.
  3. **Uso con Expresiones Regulares**:
    - Ambos métodos funcionan con expresiones regulares, pero `replace` requiere explícitamente la bandera global (`g`) para realizar múltiples reemplazos.

***

### **Conclusión**

Los métodos de reemplazo `replace` y `replaceAll` son herramientas imprescindibles para la manipulación de strings en JavaScript. Mientras que `replace` es ideal para modificaciones puntuales, `replaceAll` simplifica el trabajo con múltiples coincidencias. Entender las diferencias entre ambos y cómo aplicarlos correctamente te permitirá escribir código más eficiente y adaptable a diversas necesidades.

***

<br>
