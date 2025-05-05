---
hide:
  #- navigation
  - toc
---

<link rel="stylesheet" href="../../assets/stylesheets/javascript.css">

# **Promise.allSettled: Manejo Completo de Promesas**

El método `Promise.allSettled` en JavaScript es una herramienta diseñada para manejar múltiples promesas simultáneamente, garantizando que todas finalicen, independientemente de si se resuelven o se rechazan. A diferencia de [Promise.all](../metodo-promise-all/), que se detiene al encontrar una promesa rechazada, `.allSettled` devuelve un informe detallado con el estado y el resultado (o motivo de error) de cada promesa.

Esta capacidad es especialmente útil en situaciones donde necesitas procesar múltiples tareas en paralelo y manejar cada resultado de manera individual, incluso si algunas tareas fallan.

## **¿Qué es Promise.allSettled y cuándo usarlo?**

El método `Promise.allSettled` toma un array de promesas como entrada y devuelve una nueva promesa que se resuelve cuando todas las promesas originales han terminado. Esta promesa resultante contiene un array de objetos que describen el estado (`fulfilled` o `rejected`) y el resultado (`value` o `reason`) de cada promesa.

**sintaxis básica:**

```js linenums="1" title="javascript"
Promise.allSettled([promesa1, promesa2, promesa3])
    .then(resultados => {
        // Procesar resultados aquí
    });
```

La sintaxis básica de `Promise.allSettled` es similar a la de otros métodos de promesas. Toma un array de promesas y devuelve una nueva promesa que se resuelve con un array de objetos, cada uno con las propiedades `status` y `value` o `reason`.

### **Cuándo usar `Promise.allSettled`**

Este método es útil cuando necesitas:

  - Obtener un resumen completo de los resultados de varias operaciones, incluso si algunas fallan.
  - Ejecutar procesos en lote donde el éxito o el fallo de una tarea no detenga la ejecución general.
  - Gestionar errores de manera individual sin detener otras operaciones.

## **Ejemplo básico de uso**

Imagina que tienes tres promesas, dos de las cuales se resuelven y una falla. `Promise.allSettled` procesará todas las promesas y proporcionará un resumen de su estado.

```js linenums="1" title="javascript"
const promesa1 = Promise.resolve("Promesa 1 completada");
const promesa2 = Promise.reject("Error en Promesa 2");
const promesa3 = Promise.resolve("Promesa 3 completada");

Promise.allSettled([promesa1, promesa2, promesa3])
    .then(resultados => {
        resultados.forEach((resultado, indice) => {
        if (resultado.status === "fulfilled") {
            console.log(`Promesa ${indice + 1} resultó con éxito: ${resultado.value}`);
        } else {
            console.log(`Promesa ${indice + 1} falló: ${resultado.reason}`);
        }
        });
    });
```

Cada promesa en el array es procesada independientemente. La salida muestra un resumen de cada operación, especificando si se completó con éxito (`fulfilled`) o falló (`rejected`).

## **Procesamiento avanzado de resultados**

Puedes organizar los resultados de `Promise.allSettled` en categorías para manejarlos de manera más clara, separando las promesas exitosas de las fallidas.

```js linenums="1" title="javascript"
async function procesarResultados(promesas) {
    const resultados = await Promise.allSettled(promesas);
    const exitosas = resultados.filter(res => res.status === "fulfilled");
    const fallidas = resultados.filter(res => res.status === "rejected");

    console.log("Promesas exitosas:", exitosas.map(res => res.value));
    console.log("Promesas fallidas:", fallidas.map(res => res.reason));
}

const promesas = [
    Promise.resolve("Datos del Usuario"),
    Promise.reject("Error en el servidor"),
    Promise.resolve("Datos de la Orden")
];

procesarResultados(promesas)
```

Se utilizan funciones de filtro para clasificar los resultados según su estado. Los resultados exitosos (`fulfilled`) y fallidos (`rejected`) se procesan por separado.

## **Ventajas y consideraciones al usar Promise.allSettled**

**Procesamiento completo**: Garantiza que todas las promesas sean procesadas, incluso si algunas fallan.

**Control detallado de errores**: Permite manejar errores individualmente sin interrumpir otras operaciones.

**Ideal para lotes de tareas**: Útil cuando necesitas conocer el estado de cada tarea en un conjunto de operaciones.

## **Consideraciones**

  - **Manejo de Datos Complejo**: Los resultados incluyen tanto valores como razones de error, lo que puede requerir más lógica para el manejo de datos.
  - **Mayor Uso de Recursos**: Si algunas promesas son innecesarias cuando otra falla, Promise.race puede ser más eficiente en esos casos.

***

### **Conclusión**

`Promise.allSettled` es una herramienta valiosa para manejar múltiples promesas en paralelo sin detener el flujo de ejecución en caso de errores. Proporciona un informe completo del estado de cada promesa, lo que lo convierte en una opción ideal para tareas en lote o cuando necesitas manejar resultados y errores de manera individual.

En el próximo artículo abordaremos [Promise.any en JavaScript](../metodo-promise-any/), que devuelve la primera promesa que se resuelve con éxito, proporcionando un enfoque diferente para manejar resultados en paralelo.

***

<br>
