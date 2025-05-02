---
hide:
  #- navigation
  - toc
---

<link rel="stylesheet" href="../../assets/stylesheets/javascript.css">

# **Métodos de Transformación de Caso**

Trabajar con [cadenas de texto en JavaScript](../string/) a menudo implica ajustar el formato de mayúsculas y minúsculas para normalizar datos, validar entradas o mejorar la presentación. Los métodos de transformación de caso: `toLowerCase`, `toUpperCase`, `toLocaleLowerCase` y `toLocaleUpperCase` proporcionan formas flexibles y eficaces de cambiar el caso de un string, tanto a nivel general como respetando configuraciones locales (locale).

## **Conversión a Minúsculas: `toLowerCase`**

El método `toLowerCase()` convierte todos los caracteres de una cadena a minúsculas. Es una herramienta estándar para normalizar texto antes de realizar comparaciones, búsquedas o formateos consistentes.

```js linenums="1" title="javascript"
string.toLowerCase();
```

  - **Retorna**: Un nuevo string con todos los caracteres en minúsculas.

```js linenums="1" title="javascript"
const texto = "JavaScript ES Increíble";

console.log(texto.toLowerCase());
```

El método convierte cada carácter de `"JavaScript ES Increíble"` a su equivalente en minúsculas.

### **Características**

  1. **No modifica la cadena original**: Devuelve una nueva cadena con los caracteres en minúsculas.
  2. **Case-insensitive**: Facilita comparaciones ignorando diferencias entre mayúsculas y minúsculas.
  3. **Independiente del idioma**: Sigue un comportamiento general para todas las configuraciones locales.

**Caso de Uso**: Normalizar datos antes de compararlos.

```js linenums="1" title="javascript"
function compararCadenas(cadena1, cadena2) {
  return cadena1.toLowerCase() === cadena2.toLowerCase();
}

console.log(compararCadenas("Hola", "hola"));
```

## **Conversión a Mayúsculas: `toUpperCase`**

`toUpperCase` es el opuesto de `toLowerCase` transformando todos los caracteres de un string a mayúsculas. Es útil para formatear títulos o validar texto sin importar el caso.

```js linenums="1" title="javascript"
string.toUpperCase();
```

  - **Retorna**: Un nuevo string con todos los caracteres en mayúsculas.

```js linenums="1" title="javascript"
const texto = "JavaScript es increíble";

console.log(texto.toUpperCase());
```

El método convierte cada carácter de la cadena original a su equivalente en mayúsculas.

### **Características**

  1. **Devuelve una nueva cadena**: No altera el valor original.
  2. **Universal**: Funciona para todas las configuraciones locales.
  3. **Útil para normalización**: Facilita comparaciones y formateos uniformes.

**Caso de Uso**: Generar identificadores únicos o códigos en formato estándar.

```js linenums="1" title="javascript"
function generarCodigo(nombre) {
  return nombre.toUpperCase().slice(0, 5);
}

console.log(generarCodigo("javascript")); 
```

## **Minúsculas con Soporte Regional: `toLocaleLowerCase`**

El método `toLocaleLowerCase` es similar a `toLowerCase`, pero respeta configuraciones de idioma (locale) que pueden afectar cómo se manejan ciertos caracteres. Esto es particularmente importante en idiomas como el turco, donde las reglas para convertir `"I"` a minúsculas difieren del inglés.

```js linenums="1" title="javascript"
string.toLocaleLowerCase(locale);
```

  - **`locale` (opcional)**: Un string que representa el idioma o configuración regional, como `"en-US"` o `"tr-TR"`.
  - **Retorna**: Un nuevo string en minúsculas ajustado según el locale.

**Ejemplo Básico**

```js linenums="1" title="javascript"
const texto = "I";

console.log(texto.toLocaleLowerCase("en-US")); // "i"
console.log(texto.toLocaleLowerCase("tr-TR")); // "ı"
```

En inglés, `"I"` se convierte a `"i"`. Sin embargo, en turco, `"I"` se convierte a `"ı"`, un carácter distinto.

### **Características**

  1. **Respeto al idioma**: Ideal para lenguajes con reglas particulares (por ejemplo, el turco).
  2. **Devuelve una nueva cadena**: No modifica la cadena original.
  3. **Compatible con configuraciones regionales dinámicas**.

**Caso de Uso**: Manejo de idiomas específicos

```js linenums="1" title="javascript"
const texto = "Istanbul";
console.log(texto.toLocaleLowerCase("tr-TR")); // "ıstanbul"
```

En turco, la `I` mayúscula se convierte en `ı` (sin punto), lo cual no ocurre con `toLowerCase()`

El método `toLocaleLowerCase()` es una versión mejorada de `toLowerCase()` para aplicaciones internacionales donde las reglas lingüísticas importan.

## **Mayúsculas con Soporte Regional: `toLocaleUpperCase`**

`toLocaleUpperCase` funciona como `toUpperCase`, pero también respeta configuraciones locales para manejar caracteres especiales.

```js linenums="1" title="javascript"
string.toLocaleUpperCase(locale);
```

  - **`locale` (opcional)**: Un string que representa el idioma o configuración regional.
  - **Retorna**: Un nuevo string en mayúsculas ajustado según el locale.

**Ejemplo Básico**: Manejo de idiomas específicos

```js linenums="1" title="javascript"
const texto = "istanbul";
console.log(texto.toLocaleUpperCase("tr-TR")); // "İSTANBUL"
```

En inglés, `"i"` se convierte a `"I"`, pero en turco, `"i"` se convierte a `"İ"`, un carácter específico del idioma.

El método `toLocaleUpperCase()` garantiza que la conversión a mayúsculas sea precisa según las reglas del idioma, haciéndolo esencial para aplicaciones multilingües.

### **Características**

  1. **Conversión específica del idioma**: Respeta reglas regionales únicas (como en el turco).
  2. **Devuelve una nueva cadena**: No modifica la cadena original.
  3. **Soporte para internacionalización**.

**Caso de Uso**: Formatear títulos o encabezados según la región del usuario.

```js linenums="1" title="javascript"
function formatearTitulo(titulo, locale) {
  return titulo.toLocaleUpperCase(locale);
}

console.log(formatearTitulo("istanbul", "tr-TR")); // "İSTANBUL"
```

### **Errores Comunes y Cómo Evitarlos**

  1. **Olvidar el Efecto de los Locales en `toLocaleLowerCase` y `toLocaleUpperCase`**: Si no especificas un locale, se usará el predeterminado del entorno, lo que puede dar resultados inesperados en ciertos idiomas como el turco.
  2. **No Diferenciar entre `toLowerCase` y `toLocaleLowerCase`**: Si no trabajas con locales específicos, `toLowerCase` es suficiente y más eficiente.
  3. **Comparar Cadenas sin Normalizar el Caso**: Siempre convierte las cadenas a un caso común antes de compararlas para evitar errores por mayúsculas y minúsculas.

***

### **Conclusión**

Los métodos para cambiar el caso de strings en JavaScript son esenciales para manipular y normalizar texto:

  - Usa `toLowerCase` y `toUpperCase` para operaciones generales de cambio de caso.
  - Prefiere `toLocaleLowerCase` y `toLocaleUpperCase` cuando trabajes con configuraciones regionales que afecten caracteres específicos.

Con estos métodos, puedes garantizar que tus cadenas sean consistentes y adecuadas para diferentes contextos y audiencias.

***

<br>
