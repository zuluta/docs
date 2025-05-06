---
hide:
  #- navigation
  - toc
---

<link rel="stylesheet" href="../../assets/stylesheets/javascript.css">

# **try catch finally**

El bloque try catch finally en JavaScript amplía la funcionalidad de la estructura try…catch, permitiendo ejecutar un bloque de código adicional, sin importar si en el proceso de ejecución de la estructura ocurrió o no un error. Este enfoque es ideal para limpiar recursos o realizar tareas que deben ejecutarse siempre, como cerrar conexiones o liberar memoria.

En este artículo exploraremos cómo funciona `try...catch...finally`, ejemplos de uso y las buenas prácticas para integrarlo en tu código.

## **¿Qué es try catch finally?**

La instrucción try catch finally en JavaScript permite manejar excepciones y garantizar que un bloque de código final se ejecute siempre. Este bloque adicional, denominado `finally`, se ejecuta después de que los bloques `try` y `catch` hayan completado su ejecución, independientemente de si ocurrió un error o no.

**Sintaxis básica**

```js linenums="1" title="javascript"
try {
    // Código que puede generar errores
} catch (error) {
    // Código para manejar errores
} finally {
    // Código que siempre se ejecutará
}
```

## **Ejemplo básico: Ejecución garantizada**

En el siguiente ejemplo se demuestra cómo `finally` garantiza la ejecución de un bloque final, incluso si ocurre un error.

```js linenums="1" title="javascript"
let resultado = 0;

try {
    resultado = add(10, 20); // La función `add` no está definida
} catch (e) {
    console.log("Error capturado:", e.message);
} finally {
    console.log("Bloque finally ejecutado.");
    console.log("Resultado actual:", resultado);
}
```

**Explicación del ejemplo**

  1. Se inicializa la variable `resultado` con `0`.
  2. En el bloque `try`, se intenta ejecutar la función `add`, que no está definida, lo que genera un `ReferenceError`.
  3. El bloque `catch` captura el error y muestra el mensaje de error.
  4. El bloque `finally` se ejecuta siempre, mostrando el valor actual de `resultado`, que no cambió porque ocurrió un error.

## **Validación con un cálculo siempre ejecutado**

Cuando realizamos operaciones matemáticas como divisiones, es importante verificar que los datos sean válidos para evitar errores como dividir entre cero. En este ejemplo usaremos `try...catch...finally` para manejar este caso de manera efectiva.

Además de capturar y manejar errores, el bloque `finally` nos permitirá registrar el intento de división, asegurándonos de que siempre tengamos un registro del cálculo, incluso si algo sale mal.

```js linenums="1" title="javascript"
function dividir(a, b) {
    try {
        if (b === 0) {
            throw new Error("No se puede dividir por cero.");
        }
        return a / b;
    } catch (e) {
        console.log("Error:", e.message);
        return null;
    } finally {
        console.log(`Intento de división: ${a} / ${b}`);
    }
}

console.log("Resultado:", dividir(10, 2)); // División válida
console.log("Resultado:", dividir(10, 0)); // División por cero
```

**Explicación del ejemplo anterior:**

  1. En el bloque `try`, se verifica si el divisor (`b`) es igual a `0` y se lanza un error en ese caso.
  2. Si ocurre un error, el bloque `catch` captura el mensaje y devuelve `null`.
  3. El bloque `finally` siempre registra el intento de división, incluso si ocurrió un error.

Esta implementación combina la validación de datos con un manejo de errores claro y un registro confiable, asegurando que el programa se mantenga robusto y fácil de depurar.

## **Interacciones especiales con return**

Cuando se usan declaraciones return en los bloques `try`, `catch` y `finally`, el bloque `finally` puede sobrescribir el valor de retorno.

```js linenums="1" title="javascript"
function fn() {
    try {
        return 1;
    } catch {
        return 2;
    } finally {
        return 3;
    }
}

console.log("Resultado de fn():", fn());
```

**Explicación del ejemplo**

  1. El bloque `try` intenta devolver `1`.
  2. El bloque `finally` sobrescribe el valor de retorno con `3`, porque siempre se ejecuta después de `try` y `catch`.
  3. El valor devuelto por la función es `3`.

Este comportamiento es útil para garantizar que ciertas tareas críticas siempre se ejecuten, pero debe usarse con precaución para evitar confusiones.

## **Buenas prácticas al usar try catch finally**

  1. **Usa `finally` para limpiar recursos**: Libera memoria, cierra archivos abiertos o detén procesos en ejecución.
  2. **Evita lógica innecesaria en `finally`**: Mantén este bloque breve y enfocado en tareas esenciales.
  3. **Ten cuidado con `return` en `finally`**: Recuerda que puede sobrescribir valores de retorno del bloque `try` o `catch`.
  4. **No abuses del bloque `finally`**: No lo uses para manejar errores; su propósito principal es asegurar la ejecución de código final.

***

### **Conclusión**

El bloque `try...catch...finally` en JavaScript ofrece una solución completa para manejar errores y garantizar la ejecución de tareas críticas. Ya sea que necesites liberar recursos, registrar eventos o restablecer estados, `finally` asegura que tu código siempre se ejecute, independientemente de si hubo un error.

En el siguiente artículo exploraremos cómo usar `throw` para lanzar excepciones personalizadas en JavaScript.

***

<br>
