---
hide:
  #- navigation
  - toc
---

<link rel="stylesheet" href="../../assets/stylesheets/javascript.css">

# **Métodos de Búsqueda en Strings**

Los métodos de búsqueda en JavaScript son importantes porque nos ayudan a localizar textos dentro de un [string o cadena de caracteres](../string/), ya sea para verificar su existencia, encontrar su posición o buscar algun patrón en específico. Comprender su funcionamiento es importante para escribir código claro y eficiente.

En este artículo exploraremos los métodos de búsqueda del lenguaje. `indexOf`, `lastIndexOf`, `includes` y `search`, junto con sus casos de uso más comunes.

## **Encuentra la Primera Aparición: `indexOf()`**

El método `indexOf` nos permite buscar la posición de la primera aparición de un texto (subcadena) dentro de otra cadena. Este es un método simple pero poderoso y se utiliza comúnmente para realizar operaciones como búsqueda, validación y manipulación de texto.

```js linenums="1" title="javascript"
str.indexOf(searchValue, fromIndex)
```

  - `searchValue`: La subcadena que deseas buscar dentro de la cadena principal.
  - `fromIndex` (opcional): El índice desde donde quieres que comience la búsqueda. Si no se especifica, comienza desde el inicio de la cadena (índice 0).

><br>
> El método indexOf() devuelve el índice de la primera aparición de searchValue en la cadena. En caso de encontrar el valor buscado, devuelve -1. y un dato a tener en cuenta es que es sensible a mayúsculas y minúsculas.
>
><br>

**Búsqueda básica con indexOf:**

```js linenums="1" title="javascript"
const text = "Hola mundo";

console.log(text.indexOf("mundo")); // 5
console.log(text.indexOf("Hola"));  // 0
console.log(text.indexOf("hola"));  // -1 (sensible a mayúsculas)
```

### **Usando el segundo parámetro (fromIndex)**

Podemos especificar desde donde queremos que el método empiece la búsqueda, para esto utilizamos el parámetro numérico que establece el índice específico.

```js linenums="1" title="javascript"
const text = "Banana Banana";

console.log(text.indexOf("Banana"));       // 0
console.log(text.indexOf("Banana", 1));   // 7 (salta la primera "Banana")
console.log(text.indexOf("Banana", 8));   // -1 (no hay más "Banana" después del índice 8)
```

### **Validar si una subcadena existe**

Un uso recurrente para este metodo es la verificación de un texto en un string, dado que `indexOf` devuelve `-1` si no encuentra la subcadena, puedes usarlo para verificar si un texto esta presente dentro de esta.

```js linenums="1" title="javascript"
const text = "Frontend Developer";

if (text.indexOf("Developer") !== -1) {
    console.log("La palabra 'Developer' está presente.");
} else {
    console.log("No se encontró 'Developer'.");
}
```

### **Buenas prácticas al usar indexOf**

  1. **Comprobar con `-1`**: Asegúrate de manejar los casos donde no se encuentra la subcadena.
  2. **Trabajar con cadenas normalizadas**: Si estás buscando cadenas que pueden diferir en mayúsculas/minúsculas, normaliza antes de buscar.
  3. **Usa `fromIndex` para optimizar búsquedas repetidas**: Al buscar múltiples ocurrencias, establece un índice inicial para no buscar desde el principio cada vez.

## **Encuentra la Última Aparición: `lastIndexOf()`**

El método `lastIndexOf` es similar a `indexOf`, pero en lugar de buscar la primera aparición de una subcadena, busca la última aparición en una cadena. Este método es útil cuando necesitas identificar la posición final de un texto o caracter dentro de un string, especialmente cuando este puede aparecer múltiples veces.

```js linenums="1" title="javascript"
str.lastIndexOf(searchValue, fromIndex)
```

  - `searchValue`: La subcadena o carácter que deseas buscar dentro de la cadena principal.
  - `fromIndex` (opcional): El índice desde el cual comenzar la búsqueda, pero en este caso se realiza hacia atrás (de derecha a   izquierda). Por defecto, es la longitud de la cadena menos 1 (el final de la cadena).

><br>
> El método lastIndexOf() devuelve el índice de la última aparición de la subcadena especificada, si no encuentra la devuelve -1. Tambien es sensible a mayúsculas y minúsculas y comienza la búsqueda desde el final de la cadena (o desde el índice fromIndex especificado).
>
><br>

**Búsqueda básica con lastIndexOf:**

```js linenums="1" title="javascript"
const text = "JavaScript es asombroso, y JavaScript es popular.";
console.log(text.lastIndexOf("JavaScript")); // 27 (última aparición)
console.log(text.lastIndexOf("es"));         // 38 (última aparición)
console.log(text.lastIndexOf("z"));          // -1 (no encontrado)
```

### **Usar el segundo parámetro (fromIndex)**

Puedes especificar desde qué índice iniciar la búsqueda (hacia atrás):

```js linenums="1" title="javascript"
const text = "JavaScript es genial. JavaScript es útil.";

console.log(text.lastIndexOf("JavaScript", 20)); // 0 (busca hacia atrás desde el índice 20)
console.log(text.lastIndexOf("JavaScript", 10)); // 0 (también encuentra la primera aparición)
```

### **Ejemplo: Encontrar la última palabra o caracter en una cadena**

Si tienes una cadena de caracteres o string y quieres encontrar dónde aparece por última vez un caracter, `lastIndexOf` es una buena opción a utilizar:

```js linenums="1" title="javascript"
const url = "https://www.ejemplo.com/archivo.html";
const lastSlash = url.lastIndexOf("/");

console.log(lastSlash); // 23
console.log(url.substring(lastSlash + 1)); // "archivo.html"
```

### **Consideraciones al usar lastIndexOf**

  1. **Búsqueda ineficiente en cadenas grandes**: Al realizar búsquedas en cadenas extensas, especialmente desde un índice cercano al inicio, puede ser más costoso que `indexOf`.
  2. **No permite expresiones regulares**: Si necesitas mayor flexibilidad para buscar patrones complejos, considera usar el método `search` con expresiones regulares.

## **Verifica si un Texto Está Presente: `includes()`**

El método `includes` en JavaScript nos permite verificar si un string contiene una subcadena específica. A diferencia de otros métodos, `includes` no devuelve la posición de la coincidencia, sino un valor booleano (`true` o `false`). Este método es ideal para comprobaciones rápidas y limpias.

```js linenums="1" title="javascript"
str.includes(searchString, position)
```

  - **`searchString`**: La subcadena que deseas buscar dentro de la cadena principal.
  - **`position` (opcional)**: El índice desde el cual comenzar la búsqueda. Por defecto es 0 (inicio de la cadena).

><br>
> El metodo includes() devuelve un valor booleano: true: Si la subcadena existe dentro de la cadena principal. false: Si la subcadena no existe. Tambien es sensible a mayúsculas y minúsculas y no devuelve la posición de la subcadena, solo indica si existe o no.
>
><br>

**Ejemplo básico: Verificar la existencia de una subcadena:**

```js linenums="1" title="javascript"
const text = "JavaScript es increíble";

console.log(text.includes("JavaScript")); // true
console.log(text.includes("increíble"));  // true
console.log(text.includes("python"));     // false
```

### **Usar el segundo parámetro (position)**

Puedes especificar un índice desde donde iniciar la búsqueda:

```js linenums="1" title="javascript"
const text = "Hola mundo, bienvenido al mundo de JavaScript.";

console.log(text.includes("mundo"));           // true
console.log(text.includes("mundo", 10));        // true (busca desde el índice 10)
console.log(text.includes("bienvenido ", 25));  // false (después del índice 25 no hay "bienvenido")
```

### **Ejemplo: Validar si una palabra clave está presente**

```js linenums="1" title="javascript"
const email = "usuario@example.com";

if (email.includes("@")) {
    console.log("El correo electrónico es válido.");
} else {
    console.log("El correo electrónico no es válido.");
}
```

### **Ventajas del método includes()**

  1. **Legible y directo**: Es fácil de entender, ya que indica claramente si un texto incluye una subcadena.
  2. **Más expresivo**: Comparado con `indexOf`, no necesitas verificar si el resultado es diferente de `-1`.
  3. **Útil para validaciones**: Ideal para casos donde solo importa la presencia de una subcadena, no su posición.

## **Buscar con Expresiones Regulares: `search()`**

El método `search()` se utiliza para buscar un patrón específico dentro de una cadena de texto. Este método es poderoso porque permite el uso de expresiones regulares para definir patrones de búsqueda, lo que lo hace más flexible que métodos como `indexOf` o `includes`.

```js linenums="1" title="javascript"
str.search(regexp)
```

  - **`regexp`**: Una expresión regular (o un objeto `RegExp`) que define el patrón que deseas buscar. También puedes pasar una cadena literal, que internamente se convierte en una expresión regular.

><br>
> El método search() devuelve la posición del primer índice donde se encuentra una coincidencia con el patrón, si no encuentra ninguna coincidencia, devuelve -1. Funciona exclusivamente con patrones de búsqueda, lo que lo hace ideal para búsquedas avanzadas o casos donde indexOf no es suficiente.
>
><br>

### **Ejemplos básicos:**

**Buscar un texto literal con el método search()**

```js linenums="1" title="javascript"
const text = "JavaScript es asombroso.";

console.log(text.search("JavaScript")); // 0
console.log(text.search("es"));         // 11
console.log(text.search("Python"));     // -1 (no encontrado)
```

**Usar expresiones regulares**

```js linenums="1" title="javascript"
const text = "JavaScript es divertido.";

console.log(text.search(/divertido/));  // 14 (coincide con "divertido")
console.log(text.search(/javascript/i)); // 0 (coincide con "JavaScript", sin distinguir mayúsculas/minúsculas)
```

### **Ejemplo: Validar un formato específico**

Puedes usar `search()` para validar patrones como correos electrónicos, números de teléfono o URLs.

```js linenums="1" title="javascript"
const email = "usuario@example.com";
const emailPattern = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;

if (email.search(emailPattern) !== -1) {
    console.log("El correo es válido.");
} else {
    console.log("El correo no es válido.");
}
```

```js linenums="1" title="javascript"
const phone = "123-456-7890";
const phonePattern = /^\d{3}-\d{3}-\d{4}$/;

if (phone.search(phonePattern) !== -1) {
    console.log("El número de teléfono es válido.");
} else {
    console.log("El número de teléfono no es válido.");
}
```

### **Ventajas del método search()**

  1. **Soporte para expresiones regulares**: Esto lo hace mucho más flexible y poderoso que métodos como `indexOf`.
  2. **Intuitivo**: Aunque permite expresiones regulares complejas, su uso básico es fácil de entender.
  3. **Búsquedas avanzadas**: Puedes usar modificadores como `i` (ignorar mayúsculas), `g` (global) o patrones complejos.

### **Algunas limitaciones al utilizar el método search()**

  1. **Devuelve solo el índice de la primera coincidencia**: Si necesitas encontrar todas las coincidencias, es mejor usar el método `match` con una expresión regular global (`/patrón/g`).
  2. **No proporciona un booleano**: Si solo necesitas verificar la presencia de un patrón, `includes` es más apropiado.
  3. **Requiere expresiones regulares para búsquedas avanzadas**: Esto puede ser confuso para desarrolladores no familiarizados con las expresiones regulares.

***

### **Conclusión:**

Los métodos de búsqueda en JavaScript ofrecen soluciones versátiles para manipular texto:

  - Usa `includes` para verificaciones rápidas.
  - Prefiere `indexOf` y `lastIndexOf` para localizar posiciones exactas.
  - Utiliza `search` cuando necesites manejar patrones más complejos.

Con estos métodos disponibles podrás resolver problemas relacionados con cadenas de texto de forma efectiva y profesional.

***

<br>
