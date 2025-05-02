---
hide:
  #- navigation
  - toc
---

<link rel="stylesheet" href="../../assets/stylesheets/javascript.css">

# **Métodos de Extracción y Corte**

La manipulación de cadenas de texto o strings es una tarea muy recurrida en JavaScript, y los métodos `slice`, `substring` y `split` son herramientas clave para realizar estas operaciones. Estos métodos te permiten extraer secciones de un string o dividirlo en partes más manejables. En este artículo, exploraremos cómo funcionan, cómo se diferencian y cómo puedes utilizarlos de manera efectiva en tus proyectos.

## **Extrae una Porción de la Cadena: `slice`**

El método `slice` se utiliza para extraer una parte de un string. Recibe dos argumentos: el índice de inicio y el índice de fin (opcional). Devuelve una nueva cadena que contiene los caracteres desde el índice de inicio hasta el índice anterior al índice de fin. Si no se especifica el índice de fin, `slice` extrae desde el índice de inicio hasta el final del string.

```js linenums="1" title="javascript"
string.slice(start, end);
```

  - **`start`**: Especifica el índice desde donde comienza la extracción. Si es negativo, cuenta desde el final de la cadena, si no se especifica, comienza desde el índice `0`.
  - **`end`** (opcional): Especifica el índice donde termina la extracción (no incluye este índice). Si es negativo, cuenta desde el final, si no se especifica extrae hasta el final de la cadena.

### **Extraer una subcadena específica**

```js linenums="1" title="javascript"
const texto = "JavaScript es asombroso";

const subcadena = texto.slice(0, 10); // Desde el índice 0 hasta el 9
console.log(subcadena); // "JavaScript"
```

**Omitir el parámetro `end`**: Si no se especifica el segundo argumento, extrae desde `start` hasta el final de la cadena:

```js linenums="1" title="javascript"
const texto = "Frontend Developer";

const subcadena = texto.slice(9);
console.log(subcadena); // "Developer"
```

**Usar índices negativos**: Los índices negativos cuentan desde el final de la cadena:

```js linenums="1" title="javascript"
const texto = "JavaScript";

const subcadena = texto.slice(-10, -6); // Desde -10 (inicio) hasta -6 (no incluido)
console.log(subcadena); // "Java"
```

El método `slice` es especialmente útil cuando necesitas extraer partes específicas de una cadena, como la extensión de un archivo:

```js linenums="1" title="javascript"
function obtenerExtension(archivo) {
  return archivo.slice(archivo.lastIndexOf(".") + 1);
}

console.log(obtenerExtension("documento.txt")); // "txt"
console.log(obtenerExtension("imagen.png")); // "png"
```

En este ejemplo, el método `lastIndexOf` encuentra la posición del último punto en el nombre del archivo, y `slice` extrae todo lo que viene después, devolviendo la extensión del archivo.

### **Ventajas de `slice()`**

  1. **Seguro y no destructivo**: No altera la cadena o arreglo original.
  2. **Versatilidad**: Funciona con cadenas y arreglos, lo que lo hace adecuado para múltiples casos.
  3. **Soporte para índices negativos**: Simplifica la extracción desde el final.

## **Extrae Subcadenas de Forma Segura: substring**

El método `substring()` se utiliza para extraer una porción de una cadena entre dos índices, devolviendo una nueva cadena sin modificar la original. Es una alternativa al método `slice()` pero con algunas diferencias importantes, como el manejo de índices negativos.

```js linenums="1" title="javascript"
string.substring(start, end)
```

  - **`start`**: Índice donde comienza la extracción. Es obligatorio.
  - **`end`** (opcional): Índice donde finaliza la extracción (no incluido). Si no se especifica, extrae hasta el final de la cadena.

El método substring No modifica la cadena original, devuelve una nueva cadena con la porción extraída. Índices negativos no válidos: Si se pasa un índice negativo, se considera como `0`. Si `start` es mayor que `end` los valores se invierten automáticamente.

**No permite contar desde el final**: A diferencia de `slice()`, no acepta índices negativos.

### **Extraer una subcadena específica**

```js linenums="1" title="javascript"
const texto = "JavaScript es increíble";

const subcadena = texto.substring(0, 10); // Desde el índice 0 hasta el 9
console.log(subcadena); // "JavaScript"
```

### **Omitir el segundo argumento**

Si no se especifica el parámetro `end`, extrae desde el índice inicial hasta el final de la cadena:

```js linenums="1" title="javascript"
const texto = "Frontend Developer";

const subcadena = texto.substring(9);
console.log(subcadena); // "Developer"
```

### **Intercambio de índices**

Si `start` es mayor que `end`, `substring()` invierte los valores automáticamente:

```js linenums="1" title="javascript"
const texto = "JavaScript";

const subcadena = texto.substring(10, 4); // Se invierte a substring(4, 10)
console.log(subcadena); // "Script"
```

### **Ventajas de substring()**

  1. **Robustez**: Los índices negativos y valores fuera de rango no generan errores.
  2. **Intercambio de índices automático**: Asegura que siempre funcione, sin importar el orden de los argumentos.
  3. **Legibilidad**: Es claro y fácil de entender para tareas de extracción de texto.

## **Divide un String en Partes: `split`**

El método `split()` en JavaScript se utiliza para dividir una cadena en un arreglo de subcadenas, usando un separador especificado. Es una herramienta esencial para trabajar con datos basados en texto, como transformar una línea de texto en elementos individuales o procesar datos estructurados.

```js linenums="1" title="javascript"
string.split(separator, limit)
```

  - **`separator`**: Define cómo dividir la cadena. Puede ser: Una subcadena específica (como `","` o `" "`), una expresión regular para patrones más complejos. Si no se especifica o es `undefined`, el resultado será un arreglo con la cadena completa como único elemento.
  - **`limit`** (opcional): Un número que indica cuántas divisiones realizar. Si se especifica, el arreglo resultante tendrá un máximo de `limit` elementos.

El método split devuelve un arreglo: Cada elemento es una parte de la cadena original, no modifica la cadena original, además de retornar un nuevo arreglo.

### **Dividir una cadena con un separador simple**

```js linenums="1" title="javascript"
const texto = "manzana, pera, uva, mango";

console.log(texto.split(", ")); // ["manzana", "pera", "uva", "mango"]
console.log(texto.split(", ", 2)); // ["manzana", "pera"]
```

**Explicación:**

  1. En `texto.split(", ")`, el separador `", "` indica que el texto debe dividirse donde aparecen comas seguidas de un espacio. Esto crea un array con cada fruta como un elemento separado.
  2. Con `texto.split(", ", 2)`, se especifica un límite de 2 elementos en el array resultante. El método detiene la división después de encontrar las dos primeras coincidencias del separador.

### **Dividir sin un separador**

Si no se especifica un separador, el resultado será un arreglo con la cadena completa como único elemento:

```js linenums="1" title="javascript"
const texto = "JavaScript es genial";
const resultado = texto.split();

console.log(resultado);
```

### **Uso con Expresiones Regulares**

`split` también puede usar expresiones regulares como separadores, lo que lo hace muy flexible:

```js linenums="1" title="javascript"
const texto = "JavaScript123Python456Ruby";

console.log(texto.split(/\d+/)); // ["JavaScript", "Python", "Ruby"]
```

En este ejemplo, la expresión regular `/\d+/` divide el string en cada secuencia de uno o más dígitos (`123`, `456`), eliminándolos del resultado.

### **Ventajas de split()**

  1. **Versatilidad**: Compatible con separadores simples y patrones complejos.
  2. **Facilidad de uso**: Ideal para tareas como convertir texto en arreglos.
  3. **Compatibilidad universal**: Funciona en todos los navegadores y versiones modernas de JavaScript.

## **Diferencias Clave Entre slice, substring y split**

  1. **Propósito**:
    - `slice` y `substring` se usan para extraer una sección de un string.
    - `split` divide un string en partes y devuelve un array.
  2. **Índices Negativos**:
    - `slice` admite índices negativos, comenzando desde el final del string.
    - `substring` trata los índices negativos como `0`.
  3. **Orden de Índices**:
    - `substring` invierte los índices fuera de orden automáticamente.
    - `slice` no invierte índices; espera que estén en el orden correcto.

***

### **Conclusión**

Los métodos `slice`, `substring` y `split` son herramientas fundamentales para manipular strings en JavaScript. Cada uno tiene su propósito único:

  - Usa `slice` para trabajar con índices negativos o extraer partes específicas.
  - Prefiere `substring` cuando los índices pueden estar desordenados.
  - Adopta `split` para convertir cadenas en arrays basados en separadores.

***

<br>
