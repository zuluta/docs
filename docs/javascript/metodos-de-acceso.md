---
hide:
  #- navigation
  - toc
---

<link rel="stylesheet" href="../../assets/stylesheets/javascript.css">

# **Métodos de Acceso a Caracteres**

Los métodos de acceso a caracteres en JavaScript nos permiten trabajar con las posiciones específicas de un string, ya sea para obtener el carácter en una posición, su representación en Unicode o incluso para trabajar con índices negativos. En este artículo, exploraremos en detalle los métodos `charAt`, `charCodeAt`, `codePointAt` y `at`.

## **Obtén el Carácter en una Posición: `charAt`**

El método `charAt` devuelve el carácter ubicado en una posición específica de un string. Si el índice está fuera de rango, devuelve una cadena vacía (`""`).

```js linenums="1" title="javascript"
str.charAt(index)
```

  - **`index`**: Es un número entero que indica la posición del carácter que deseas obtener. El índice comienza desde `0` (el primer carácter de la cadena).

Si el índice está fuera de los límites (menor que `0` o mayor o igual al tamaño de la cadena) devuelve una cadena vacía (`""`). Este es uno de los métodos de acceso que ofrece una alternativa a la notación de corchetes (`str[index]`), que realiza una tarea similar pero con un comportamiento más predecible en navegadores más antiguos.

### **Obtener un carácter en una posición específica**

```js linenums="1" title="javascript"
const text = "JavaScript";

console.log(text.charAt(0)); // "J" (primer carácter)
console.log(text.charAt(4)); // "S" (quinto carácter)
console.log(text.charAt(10)); // "" (índice fuera de rango)
```

En el anterior ejemplo el método con el argumento `0` devuelve el primer carácter, `"J"`. con el argumento `4` devuelve el carácter `"S"`. Un índice fuera del rango devuelve una cadena vacía.

**Ejemplo 1: Convertir el primer carácter a mayúscula**: Puedes usar `charAt()` para manipular el primer carácter de una cadena.

```js linenums="1" title="javascript"
const text = "javascript";
const capitalized = text.charAt(0).toUpperCase() + text.slice(1);

console.log(capitalized); // "Javascript"
```

**Ejemplo 2: Verificar si un carácter es un número**: Puedes verificar si un carácter en una posición específica es un número.

```js linenums="1" title="javascript"
const code = "A12345";
const char = code.charAt(1);
if (!isNaN(char)) {
    console.log(`El carácter '${char}' es un número.`);
} else {
    console.log(`El carácter '${char}' no es un número.`);
}
```

### **Ventajas del uso de `charAt()`**

  1. **Compatibilidad universal**: Es compatible incluso con navegadores antiguos.
  2. **Claridad y legibilidad**: Es explícito en su propósito de obtener un carácter en una posición específica.
  3. **Predecible**: Retorna una cadena vacía (`""`) si el índice está fuera de rango, lo que facilita el manejo de errores.

## **Código Unicode del Carácter: `charCodeAt`**

El método `charCodeAt` se utiliza para obtener el código Unicode del carácter en una posición específica dentro de un string. Este método es esencial cuando necesitas trabajar con valores numéricos que representan caracteres, como codificaciones o comparaciones.

```js linenums="1" title="javascript"
string.charCodeAt(index);
```

  - **'index`**: Es un número entero que indica la posición del carácter en la cadena. El índice comienza en `0`.

El método devuelve el código Unicode (número entre 0 y 65535) del carácter en la posición especificada. Si el índice está fuera de los límites de la cadena (menor que 0 o mayor o igual al tamaño de la cadena), devuelve `NaN`. El valor devuelto corresponde al punto de código de Unicode del carácter (UTF-16).

### **Obtener el código Unicode de un carácter**

```js linenums="1" title="javascript"
const text = "Hola";

console.log(text.charCodeAt(0)); // 72 (código de 'H')
console.log(text.charCodeAt(1)); // 111 (código de 'o')
console.log(text.charCodeAt(10)); // NaN (índice fuera de rango)
```

Puedes usar el método complementario `String.fromCharCode()` para convertir un código en un carácter:

```js linenums="1" title="javascript"
const code = 72;

console.log(String.fromCharCode(code)); // "H"
```

**Ejemplo: Recorrer una cadena y obtener los códigos Unicode**: Puedes usar un bucle para iterar sobre cada carácter de la cadena y obtener su código Unicode:

```js linenums="1" title="javascript"
const text = "ABC";

for (let i = 0; i < text.length; i++) {
    console.log(`Carácter: ${text.charAt(i)}, Código: ${text.charCodeAt(i)}`);
}
```

**Ejemplo: Recorrer una cadena y obtener los códigos Unicode**: Puedes usar un bucle para iterar sobre cada carácter de la cadena y obtener su código Unicode:

```js linenums="1" title="javascript"
const text = "ABC";
for (let i = 0; i < text.length; i++) {
    console.log(`Carácter: ${text.charAt(i)}, Código: ${text.charCodeAt(i)}`);
}
// Resultado:
// Carácter: A, Código: 65
// Carácter: B, Código: 66
// Carácter: C, Código: 67
```

### **Ventajas del método `charCodeAt()`**

**Sencillo y eficiente**: Es una forma directa de acceder al valor Unicode de un carácter.
**Compatibilidad universal**: Funciona con todos los navegadores modernos y antiguos.
**Ideal para validaciones y transformaciones**: Útil en tareas como la validación de entradas o encriptación básica.

## **Valor Unicode Avanzado: `codePointAt`**

El método `codePointAt()` se utiliza para obtener el valor Unicode completo (punto de código) de un carácter en una posición específica de una cadena. Este método es especialmente útil para trabajar con caracteres fuera del rango básico de Unicode (como emojis o símbolos especiales), que no pueden representarse con un solo valor de 16 bits en UTF-16.

```js linenums="1" title="javascript"
string.codePointAt(index);
```

  - **`index`**: Es un número entero que indica la posición del carácter en la cadena. El índice comienza desde `0`.

El método `codePointAt` devuelve el punto de código Unicode completo de un carácter, incluso si está representado como un par sustituto en UTF-16. Es útil para caracteres que tienen valores mayores a `U+FFFF`. Si el índice está fuera del rango de la cadena, devuelve `undefined`.

### **Obtener el valor Unicode de un carácter**

```js linenums="1" title="javascript"
const text = "Hola";

console.log(text.codePointAt(0)); // 72 (código de 'H')
console.log(text.codePointAt(1)); // 111 (código de 'o')
console.log(text.codePointAt(10)); // undefined (índice fuera de rango)
```

### **Diferencias entre `charCodeAt()` y `codePointAt()`**

El método `charCodeAt()` solo devuelve la primera parte de un par sustituto, mientras que `codePointAt()` maneja correctamente los puntos de código suplementarios.

```js linenums="1" title="javascript"
const emoji = "😄";

console.log(emoji.charCodeAt(0)); // 55357 (primera parte del par sustituto)
console.log(emoji.charCodeAt(1)); // 56836 (segunda parte del par sustituto)

console.log(emoji.codePointAt(0)); // 128516 (valor completo del emoji)
```

**Ejemplo: Detectar caracteres fuera del rango básico**

```js linenums="1" title="javascript"
const text = "A😄B";
for (let i = 0; i < text.length; i++) {
    const code = text.codePointAt(i);
    if (code > 65535) {
        console.log(`Carácter avanzado detectado: ${text[i]}, Código: ${code}`);
        i++; // Saltar la segunda parte del par sustituto
    } else {
        console.log(`Carácter: ${text[i]}, Código: ${code}`);
    }
}
```

### **Ventajas de `codePointAt()`**

  - **Compatibilidad con caracteres avanzados**: Funciona perfectamente con caracteres suplementarios (por encima de `U+FFFF`).
  - **Evita errores con pares sustitutos**: A diferencia de `charCodeAt()`, no es necesario combinar manualmente las partes de un par sustituto.
  - **Integración con `String.fromCodePoint()`**: Permite una conversión bidireccional sencilla entre puntos de código y caracteres.

## **Acceso Simplificado (Con Índices Negativos): `at`**

El método `at` proporciona una forma simplificada y moderna de acceder a los elementos de un string y arreglos con soporte para índices negativos. Fue introducido en **ECMAScript 2022** y ofrece una alternativa más clara y funcional a la notación de corchetes (`[]`) o métodos tradicionales como `charAt()`.

```js linenums="1" title="javascript"
string.at(index);
```
  - **`index`**: Es un número entero que indica la posición del elemento que deseas obtener. Puede ser positivo (desde el inicio) o negativo (desde el final).

Este método permite acceder a los elementos desde el final de la cadena o arreglo, sin necesidad de calcular manualmente la longitud. Devuelve el carácter o elemento en la posición especificada, funciona tanto en cadenas como en arreglos. Si el índice está fuera de rango, devuelve `undefined` (en lugar de una cadena vacía como `charAt()`).

### **Acceder a caracteres en cadenas**

```js linenums="1" title="javascript"
const text = "JavaScript";

console.log(text.at(0));  // "J" (primer carácter)
console.log(text.at(4));  // "S" (quinto carácter)
console.log(text.at(-1)); // "t" (último carácter)
console.log(text.at(-3)); // "i" (tercer carácter desde el final)
console.log(text.at(20)); // undefined (índice fuera de rango)
```

**Acceder a elementos en arreglos:**

```js linenums="1" title="javascript"
const array = [10, 20, 30, 40, 50];

console.log(array.at(0));  // 10 (primer elemento)
console.log(array.at(-1)); // 50 (último elemento)
console.log(array.at(-2)); // 40 (penúltimo elemento)
console.log(array.at(10)); // undefined (índice fuera de rango)
```

### **Ventajas de usar `at()`**

  - **\1. Soporte para índices negativos**: El método `at()` simplifica el acceso a elementos desde el final de una cadena o arreglo. Con métodos anteriores, esto requería cálculos manuales con la longitud.
  - **Comportamiento predecible**: A diferencia de `charAt()`, que devuelve una cadena vacía si el índice está fuera de rango, `at()` devuelve `undefined`, lo que facilita la detección de errores.
  - **Compatibilidad con arreglos**: El soporte para cadenas y arreglos hace que sea una solución unificada y más legible.

***

### **Conclusión**

Los métodos de acceso a caracteres en JavaScript son herramientas fundamentales para trabajar con strings a nivel granular:

  - Usa `charAt` o `at` para obtener caracteres individuales, con índices positivos o negativos.
  - Prefiere `charCodeAt` y `codePointAt` cuando necesites información sobre valores Unicode.
  - Adopta `normalize` para trabajar con texto multilingüe o evitar inconsistencias en caracteres similares.

Conocer estos métodos te permitirá manejar texto de manera más precisa y eficiente en tus proyectos.

***

<br>
