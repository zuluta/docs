---
hide:
  #- navigation
  - toc
---

<link rel="stylesheet" href="../../assets/stylesheets/javascript.css">

# **try catch**

El manejo de errores en JavaScript es importante al momento de construir aplicaciones confiables y robustas. La instrucción try catch permite ejecutar bloques de código que podrían generar errores y manejar dichos errores de manera controlada. Esto no solo previene bloqueos inesperados en tu programa, sino que también asegura una experiencia más fluida para el usuario.

En este artículo exploraremos cómo funciona `try...catch`, con ejemplos y explicaciones para que entiendas su funcionamiento.

## **¿Qué es try catch?**

`try...catch` es una estructura de control que te permite identificar errores en tiempo de ejecución y manejarlos sin detener la ejecución del programa. Si ocurre un error en el bloque `try`, el control pasa al bloque `catch`, donde puedes capturar el error y decidir cómo manejarlo.

**Sintaxis básica**

```js linenums="1" title="javascript"
try {
    // Código que podría generar un error
} catch (error) {
    // Código para manejar el error
}
```

El bloque `try` contiene el código que deseas ejecutar. Si se genera un error, el control pasa al bloque `catch`, donde el objeto `error` proporciona detalles sobre lo que ocurrió.

## **Ejemplo básico: Llamada a una función inexistente**

```js linenums="1" title="javascript"
try {
    let resultado = suma(10, 20); // La función `suma` no está definida
    console.log("Resultado:", resultado);
} catch (error) {
    console.log("Error capturado:");
    console.log("Nombre del error:", error.name);
    console.log("Mensaje del error:", error.message);
}

console.log("El programa continúa ejecutándose.");
```

En este caso, intentamos ejecutar una función llamada `suma` que no está definida. Esto genera un error de tipo `ReferenceError`. Sin `try catch`, el programa se detendría abruptamente, pero gracias a la estructura:

  1. El bloque `try` intenta ejecutar la operación y encuentra el error.
  2. El control pasa al bloque `catch`, donde capturamos el error y mostramos detalles relevantes (`name` y `message`) usando `console.log`.
  3. Finalmente, el mensaje “El programa continúa ejecutándose” demuestra que el programa no se interrumpió y puede seguir funcionando normalmente.

### **Cómo usar try catch para validar datos**

Uno de los casos más comunes para `try...catch` es validar datos que podrían ser incorrectos o estar mal formateados. Por ejemplo, al analizar cadenas JSON, un formato inválido generará un error.

```js linenums="1" title="javascript"
try {
    let datos = JSON.parse('{"nombre": "JavaScript"}'); // JSON válido
    console.log("Datos analizados:", datos);
} catch (error) {
    console.log("Error al analizar JSON:", error.message);
}
```

En el código anterior la cadena JSON es válida, por lo que el bloque `try` se ejecuta sin problemas, y el resultado del análisis se muestra en consola. Si la cadena JSON hubiera sido inválida, el bloque `catch` manejaría el error generado por `JSON.parse`.

Este patrón es útil para prevenir errores en datos externos o de usuarios que podrían romper tu programa si no se validan correctamente.

## **Ejemplo: Manejo de entradas no válidas**

Cuando se trabaja con funciones que procesan datos dinámicos, como entradas de usuarios o cálculos matemáticos, es importante validar esos datos antes de realizar cualquier operación. En el siguiente ejemplo veremos cómo usar try catch para manejar entradas no válidas y lanzar errores personalizados que describan exactamente lo que salió mal.

```js linenums="1" title="javascript"
function dividir(a, b) {
    if (b === 0) {
        throw new Error("No se puede dividir por cero.");
    }
    return a / b;
}

try {
    console.log("Resultado:", dividir(10, 0));
} catch (error) {
    console.log("Error capturado:", error.message);
}
```

En el código anterior:

  1. Creamos una función llamada `dividir` que lanza un error con `throw` si el divisor (`b`) es igual a cero.
  2. En el bloque `try`, llamamos a `dividir` con `b = 0`, lo que genera un error personalizado.
  3. El bloque `catch` captura el error y muestra su mensaje.

El uso de `throw` permite lanzar errores personalizados, proporcionando descripciones claras para situaciones específicas. Este enfoque es ideal para validar datos de entrada y evitar cálculos matemáticos erróneos.

## **Buenas prácticas al usar try catch**

  1. **Coloca solo el código propenso a errores en el bloque try**: Evita envolver bloques grandes de código innecesariamente, ya que dificulta el manejo específico de errores.

```js linenums="1" title="javascript"
try {
     datos = JSON.parse(cadenaInvalida);
} catch (error) {
    console.error("Error al analizar JSON:", error.message);
}
```

  2. **Proporciona mensajes significativos**: Al manejar errores, asegúrate de ofrecer información clara sobre lo que salió mal.

  3. **Evita depender de `try catch` para lógica normal**: No uses `try...catch` como una solución predeterminada para el flujo lógico. Diseña tu código para prevenir errores siempre que sea posible.

## **Errores comunes al usar try…catch**

  1. **Capturar errores irrelevantes**: Si el bloque `try` es demasiado amplio, puedes terminar manejando errores que no están relacionados con el propósito de tu código.
  2. **Ignorar el objeto `error`**: No usar el objeto `error` en el bloque `catch` desperdicia información valiosa sobre lo que ocurrió.
  3. **Falta de validación previa**: Muchas veces los errores pueden evitarse validando las entradas o usando estructuras condicionales antes de llegar al bloque `try`.

***

### **Conclusión**

La instrucción `try...catch` en JavaScript es una herramienta indispensable para manejar errores y garantizar la estabilidad de tus aplicaciones. Al capturar y gestionar excepciones, puedes evitar bloqueos inesperados y mejorar la experiencia del usuario. Sin embargo, es importante usar `try...catch` de manera estratégica, asegurándote de seguir las buenas prácticas para mantener un código limpio y manejable.

En el siguiente artículo exploraremos [try…catch…finally](../try-catch-finally/), una extensión de esta estructura que permite realizar tareas finales independientemente de si ocurrió un error o no.

***

<br>
