---
hide:
  #- navigation
  - toc
---

<link rel="stylesheet" href="../../assets/stylesheets/javascript.css">

# **Manejo de Errores en Promesas**

Trabajar con [promesas en JavaScript](../promesas/) permite manejar operaciones asíncronas de manera fluida, pero es fundamental capturar y gestionar adecuadamente los errores para evitar comportamientos inesperados y hacer el código más seguro.

En este artículo veremos cómo manejar errores en promesas usando [`catch`](../try-catch/), `finally` y algunos patrones recomendados para lograr un flujo de trabajo confiable.

## **Captura Básica de Errores con catch()**

El método `catch()` es el enfoque más directo para gestionar errores en promesas. Cuando una promesa falla (es rechazada) el flujo se redirige al bloque `catch()`, donde podemos capturar el error y tomar medidas adecuadas, como mostrar un mensaje de error o registrar el problema para futuras referencias.

**Ejemplo de Captura de Errores con catch()**

```js linenums="1" title="javascript"
const promesaFallida = new Promise((resolve, reject) => {
    const exito = false;

    if (exito) {
        resolve("Operación exitosa");
    } else {
        reject("Ocurrió un error");
    }
});

promesaFallida
    .then(resultado => console.log("Resultado:", resultado))
    .catch(error => console.log("Error capturado:", error));
```

En este caso, como la promesa se rechaza, el flujo se redirige al bloque `catch()` capturando el error y evitando que el programa falle.

## **Uso de finally() para Ejecución Final**

El método `finally()` se ejecuta independientemente de si la promesa fue resuelta o rechazada, permitiendo ejecutar tareas de limpieza o finalizar acciones sin importar el resultado de la operación.

**Ejemplo de Uso de finally()**

```js linenums="1" title="javascript"
const promesa = new Promise((resolve, reject) => {
    const exito = false;
    
    if (exito) {
        resolve("Operación exitosa");
    } else {
        reject("Ocurrió un error");
    }
});

promesa
    .then(resultado => console.log("Resultado:", resultado))
    .catch(error => console.log("Error capturado:", error))
    .finally(() => console.log("Operación finalizada"));
```

En este ejemplo, el `finally()` asegura que el mensaje “Operación finalizada” se imprima independientemente del éxito o fallo de la promesa.

## **Propagación de Errores en Cadena de Promesas**

Al encadenar múltiples promesas, si una falla, los errores se propagan por la cadena hasta el primer bloque `catch()` disponible. Esto simplifica el manejo de errores en operaciones secuenciales, ya que no es necesario capturar errores en cada paso de la cadena.

**Ejemplo de Propagación de Errores**

```js linenums="1" title="javascript"
const promesa = new Promise((resolve, reject) => {
  resolve(5);
});

promesa
    .then(resultado => {
        console.log("Resultado inicial:", resultado);
        return resultado * 2;
    })
    .then(doble => {
        console.log("Doble:", doble);
        throw new Error("Error en la operación");
    })
    .then(triple => {
        console.log("Este código no se ejecutará");
    })
    .catch(error => console.log("Error capturado:", error.message));
```

En el código anterior el error lanzado en el segundo then es capturado por el `catch()` al final de la cadena.

## **Manejo de Errores Condicionales**

Es posible gestionar errores específicos basados en el tipo de error o en su mensaje, permitiendo reacciones diferentes para cada tipo de fallo. Este enfoque es útil en situaciones en las que ciertos errores requieren una respuesta particular o reintentos.

**Ejemplo de Manejo Condicional de Errores**

```js linenums="1" title="javascript"
const promesa = new Promise((_, reject) => {
    reject(new Error("Error de red"));
});

promesa
    .catch(error => {
        if (error.message.includes("red")) {
        console.log("Error de red capturado, reintentando...");
        // Aquí se podría iniciar un reintento
        } else {
        console.log("Otro tipo de error:", error.message);
        }
    });
```

Este patrón ayuda a capturar y tratar los errores de manera específica, asegurando que cada error sea gestionado correctamente.

## **Error Handling Pattern: Encapsulación con Funciones Asíncronas**

Cuando manejamos muchas promesas en paralelo o en cadena, encapsular el manejo de errores en una función específica ayuda a mantener el código organizado y facilita la reutilización.

**Ejemplo de Encapsulación con Funciones de Manejo de Errores**

```js linenums="1" title="javascript"
function manejarErrores(p) {
    return p.catch(error => {
        console.error("Error capturado:", error.message);
        return null;  // Retorna un valor seguro en caso de error
    });
}

const promesa1 = manejarErrores(new Promise((_, reject) => reject(new Error("Fallo en promesa 1"))));
const promesa2 = manejarErrores(Promise.resolve("Promesa 2 exitosa"));

Promise.all([promesa1, promesa2])
    .then(resultados => {
        console.log("Resultados:", resultados);
    });
```

En este ejemplo, cada promesa es manejada por `manejarErrores()`, que captura cualquier error y retorna un valor predeterminado para que el flujo continúe sin interrupciones.

## **Buenas Prácticas para el Manejo de Errores en Promesas**

Para un manejo de errores eficaz en promesas, considera las siguientes buenas prácticas:

  1. Utiliza `catch` para Capturar Errores de Toda la Cadena: Coloca `catch` al final de la cadena de promesas para capturar cualquier error propagado.
  2. Usa `finally` para Tareas de Limpieza: Aprovecha `finally` para liberar recursos o ejecutar acciones finales sin importar el éxito o fallo de la promesa.
  3. Encapsula Errores en Funciones: En proyectos complejos, encapsular el manejo de errores en funciones específicas mejora la legibilidad y la organización del código.

***

### **Conclusión**

Manejar errores en promesas es esencial para escribir código robusto y confiable en JavaScript. Al combinar `catch`, `finally`, y patrones avanzados, puedes garantizar que el flujo de tu aplicación siga funcionando correctamente incluso en presencia de fallos. Estos enfoques mejoran la legibilidad del código y reducen la posibilidad de errores inesperados.

En el siguiente artículo exploraremos [async/await en JavaScript](../async-await/), que ofrece una forma aún más sencilla de manejar operaciones asíncronas y mejorar la claridad del código.

***

<br>
