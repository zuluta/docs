---
hide:
  #- navigation
  - toc
---

<link rel="stylesheet" href="../../assets/stylesheets/javascript.css">

# **Promise.all: Promesas en Paralelo**

El método `Promise.all` en JavaScript es una herramienta poderosa para manejar múltiples operaciones asíncronas que se ejecutan en paralelo. Es útil cuando necesitas realizar tareas que pueden completarse de manera independiente, pero deseas esperar a que todas finalicen antes de continuar con el flujo del programa.

Si todas las promesas se resuelven con éxito, `Promise.all` devuelve una nueva promesa que se resuelve con un array de resultados en el mismo orden en que las promesas fueron proporcionadas. Sin embargo, si alguna promesa falla, se rechazará con el motivo de error de la primera promesa que no se resolvió.

### **Sintaxis básica de Promise.all**

El método toma un array de promesas como entrada y devuelve una nueva promesa que espera a que todas las promesas proporcionadas se completen.

```js linenums="1" title="javascript"
Promise.all([promesa1, promesa2, promesa3])
    .then(resultados => {
        // Manejar los resultados de todas las promesas
    })
    .catch(error => {
        // Manejar el error si alguna promesa falla
    });
```

El método toma un array de promesas y devuelve una nueva promesa que se resuelve con un array de resultados cuando todas las promesas se han completado con éxito.

## **Casos comunes de uso**

  1. **Solicitar datos de múltiples fuentes**: Realizar múltiples solicitudes HTTP y procesar las respuestas una vez que todas estén disponibles.
  2. **Cargar recursos simultáneamente**: Cargar imágenes, scripts o datos de manera concurrente para optimizar el rendimiento.
  3. **Validaciones paralelas**: Ejecutar varias validaciones o cálculos en paralelo y procesar los resultados cuando todas las tareas finalicen.

### **Ejemplo básico: Ejecutar promesas en paralelo**

Supongamos que tienes tres operaciones asíncronas que tardan diferentes tiempos en completarse:

```js linenums="1" title="javascript"
const promesa1 = new Promise(resolve => setTimeout(() => resolve('Resultado 1'), 1000));
const promesa2 = new Promise(resolve => setTimeout(() => resolve('Resultado 2'), 2000));
const promesa3 = new Promise(resolve => setTimeout(() => resolve('Resultado 3'), 1500));

Promise.all([promesa1, promesa2, promesa3])
    .then(resultados => {
        console.log(resultados); // ['Resultado 1', 'Resultado 2', 'Resultado 3']
    })
    .catch(error => {
        console.log("Error en alguna de las promesas:", error);
    });

```

En este ejemplo las tres promesas se ejecutan en paralelo y el código en el bloque `then` se ejecuta una vez que todas han terminado. Si alguna promesa falla, el `catch` manejará el error.

### **¿Qué pasa si alguna promesa falla?**

Si una de las promesas en el array es rechazada, la operación se rechazará con el motivo de esa promesa.

```js linenums="1" title="javascript"
const promesaExitosa = Promise.resolve("Éxito");
const promesaFallida = Promise.reject("Fallo");

Promise.all([promesaExitosa, promesaFallida])
    .then(resultados => {
        console.log(resultados); // No se ejecutará
    })
    .catch(error => {
        console.log("Error capturado:", error); // Error capturado: Fallo
    });
```

## **Uso de Promise.all con async/await**

`Promise.all` también puede usarse en funciones asíncronas con `async/await`, lo que hace que el código sea más legible y fácil de manejar.

```js linenums="1" title="javascript"
async function cargarDatos() {
    try {
        const [usuario, ordenes, productos] = await Promise.all([
        obtenerDatosUsuario(),
        obtenerDatosOrdenes(),
        obtenerDatosProductos()
        ]);

        console.log("Datos del usuario:", usuario);
        console.log("Datos de las órdenes:", ordenes);
        console.log("Datos de los productos:", productos);
    } catch (error) {
        console.log("Error al cargar los datos:", error);
    }
}
```

En este ejemplo:

  - Las funciones `obtenerDatosUsuario`, `obtenerDatosOrdenes` y `obtenerDatosProductos` se ejecutan en paralelo.
  - Los resultados se asignan a variables en el orden en que se definieron en el array.

## **Consideraciones importantes al usar Promise.all**

**Orden de los resultados**: Aunque las promesas se ejecutan en paralelo, los resultados en el array están garantizados en el orden en que las promesas fueron pasadas a `Promise.all`.

**No es ideal para dependencias**: Si necesitas que una tarea dependa de los resultados de otra, usa encadenamiento en lugar de `Promise.all`.

**Manejo de errores**: Captura los errores correctamente con `.catch()` o `try/catch` para evitar que el programa falle inesperadamente.

## **Buenas prácticas**

  - **Asegúrate de que todas las promesas sean necesarias**: Si algunas tareas no dependen entre sí, evita incluirlas en un `Promise.all` para simplificar la lógica.
  - **Controla los errores de manera adecuada**: Diseña tu lógica para manejar fallos parciales si es necesario.
  - **Usa `async/await` para mayor claridad**: Combina `Promise.all` con `async/await` para un código más legible.

***

### **Conclusión**

El método `Promise.all` es una herramienta fundamental en JavaScript para manejar múltiples promesas en paralelo. Es ideal para optimizar operaciones asíncronas que pueden ejecutarse de manera independiente, reduciendo el tiempo total de espera. Al comprender cómo funciona y manejar adecuadamente los errores, puedes mejorar significativamente la eficiencia de tus aplicaciones.

En el próximo artículo, abordaremos [Promise.race en JavaScript](../metodo-promise-race/), que permite manejar la primera promesa que se resuelva o rechace, ofreciendo una forma diferente de manejar la asincronía.

***

<br>
