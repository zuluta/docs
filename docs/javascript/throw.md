---
hide:
  #- navigation
  - toc
---

<link rel="stylesheet" href="../../assets/stylesheets/javascript.css">

# **Lanzar Excepciones con throw**

El manejo de errores en JavaScript no solo implica capturar problemas con try…catch, sino también lanzar excepciones cuando se detectan situaciones inválidas o inesperadas. El uso de la instrucción `throw` permite detener la ejecución de un programa y definir un mensaje de error o un objeto de excepción que detalla lo ocurrido.

En este artículo exploraremos cómo usar `throw` para manejar errores de manera proactiva y cómo personalizar los mensajes para mejorar la depuración y la experiencia del usuario.

## **¿Qué es la instrucción throw en JavaScript?**

La instrucción `throw` en JavaScript se utiliza para lanzar excepciones, las cuales pueden ser manejadas con un bloque `try...catch`. Cuando el motor de JavaScript encuentra una instrucción `throw` pasa lo siguiente:

  1. Detiene inmediatamente la ejecución del código en el bloque actual.
  2. Busca el bloque `catch` más cercano en la pila de llamadas.
  3. Si no encuentra un bloque `catch`, el script se detiene y el error se muestra en la consola.

### **Sintaxis básica:**

```js linenums="1" title="javascript"
throw expresión;
```

`expresión`: Define el valor de la excepción. Puede ser un string, un número, un objeto o una instancia de la clase `Error`.

## **Ejemplo básico: Lanzar excepciones con throw**

En muchas situaciones es necesario detener la ejecución de una función si las entradas proporcionadas no cumplen con las expectativas. `throw` permite lanzar una excepción en estos casos, proporcionando un mensaje descriptivo que facilita identificar el problema.

En el siguiente ejemplo validamos los argumentos de una función `sumar`. Si los argumentos no son números, se generará una excepción con un mensaje claro que será manejado en un bloque `try...catch`.

```js linenums="1" title="javascript"
function sumar(x, y) {
    if (typeof x !== 'number') {
        throw 'El primer argumento debe ser un número';
    }
    if (typeof y !== 'number') {
        throw 'El segundo argumento debe ser un número';
    }
    return x + y;
}

try {
    const resultado = sumar('a', 10); // Error: El primer argumento no es un número
    console.log("Resultado:", resultado);
} catch (error) {
    console.log("Error capturado:", error);
}
```

**Explicación del ejemplo**

  1. La función `sumar` valida los tipos de sus argumentos con `typeof`.
  2. Si algún argumento no es un número, lanza una excepción con `throw` y un mensaje descriptivo.
  3. El bloque `try` intenta ejecutar la función, pero al detectar un error, el control pasa al bloque `catch`, donde se captura y muestra el mensaje.

Este ejemplo muestra cómo `throw` puede ser una herramienta eficaz para validar datos y detener el flujo cuando las entradas no son válidas, lo que resulta en un programa más robusto y confiable.

## **Usando throw con objetos de la clase Error**

Es común usar instancias de la clase `Error` en lugar de cadenas simples para lanzar excepciones, ya que estas proporcionan más contexto, como el nombre del error y un mensaje detallado.

```js linenums="1" title="javascript"
function dividir(a, b) {
    if (b === 0) {
        throw new Error("No se puede dividir por cero.");
    }
    return a / b;
}

try {
    const resultado = dividir(10, 0);
    console.log("Resultado:", resultado);
} catch (error) {
    console.log(error.name + ":", error.message);
}
```

**Explicación del ejemplo**

  1. Si el divisor es igual a cero, se lanza un objeto de la clase `Error` con un mensaje descriptivo.
  2. El bloque `catch` captura la excepción y accede a las propiedades `name` y `message` para mostrar un mensaje claro.

Usar objetos `Error` facilita la identificación y manejo de excepciones en aplicaciones complejas.

## **Crear excepciones personalizadas**

En algunos casos, puede ser útil crear clases personalizadas para manejar errores específicos en tu aplicación. Esto permite distinguir entre diferentes tipos de excepciones.

```js linenums="1" title="javascript"
class NumberError extends Error {
    constructor(valor) {
        super(`"${valor}" no es un número válido.`);
        this.name = "NumberError";
    }
}

function validarNumero(valor) {
    if (typeof valor !== 'number') {
        throw new NumberError(valor);
    }
}

try {
    validarNumero("texto");
} catch (error) {
    console.log(error.name + ":", error.message);
}
```

**Explicación del ejemplo**

  1. Se define la clase `NumberError` que extiende la clase `Error` y personaliza su mensaje.
  2. En la función `validarNumero`, se lanza una instancia de `NumberError` si el argumento no es un número.
  3. El bloque `catch` captura la excepción personalizada y muestra su tipo (`name`) y mensaje.

Este enfoque permite manejar errores de manera más específica, facilitando el diseño de sistemas robustos y escalables.

## **Buenas prácticas al usar throw**

  1. **Usa mensajes claros y descriptivos**: Asegúrate de que los mensajes de las excepciones expliquen claramente el problema y cómo solucionarlo.
  2. **Prefiere objetos `Error`**: Usar objetos `Error` en lugar de cadenas simples proporciona más contexto y facilita la depuración.
  3. **Distingue tipos de errores**: Si tu aplicación tiene múltiples tipos de errores, considera usar clases personalizadas para diferenciarlos.
  4. **No abuses de `throw`**: Úsalo solo para errores que realmente interrumpan el flujo lógico del programa. Para casos menores, considera validaciones simples.

***

### **Conclusión**

La instrucción `throw` en JavaScript es una herramienta poderosa para manejar errores de manera proactiva, permitiendo detener la ejecución cuando algo no va como se espera. Desde lanzar excepciones con mensajes personalizados hasta crear clases específicas para errores, el uso adecuado de `throw` puede hacer que tus aplicaciones sean más robustas y fáciles de depurar.

***

<br>
