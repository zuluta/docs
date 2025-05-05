---
hide:
  #- navigation
  - toc
---

<link rel="stylesheet" href="../../assets/stylesheets/javascript.css">

# **Promise.any: Esperando la Primera Promesa Resuelta con Éxito**

`Promise.any` es un método en JavaScript que devuelve la primera promesa que se resuelve con éxito entre varias promesas dadas. A diferencia del [método Promise.race](../metodo-promise-race/) que devuelve el primer resultado (ya sea éxito o error), este método solo se resuelve si al menos una de las promesas se completa satisfactoriamente.

Si todas las promesas fallan, el método se rechaza con un `AggregateError`, que proporciona un detalle de todos los errores.

## **¿Qué es Promise.any y Cuándo Usarlo?**

Este método aplicado a promesas es útil en situaciones donde solo necesitas el primer resultado exitoso entre varias promesas y puedes ignorar cualquier fallo que ocurra. Por ejemplo, en aplicaciones web con múltiples servidores, `Promise.any` permite obtener el primer dato disponible sin importar si otros servidores fallan o responden lentamente.

**sintaxis básica:**

```js linenums="1" title="javascript"
Promise.any([promesa1, promesa2, promesa3])
    .then(resultado => {
        // Maneja el primer resultado exitoso
    })
    .catch(error => {
        // Maneja el error si todas las promesas fallan
    });
```

La sintaxis básica de `Promise.any` es similar a otros métodos de promesas. Toma un array de promesas y devuelve una nueva promesa que se resuelve con el primer resultado exitoso o se rechaza si todas fallan.

**Casos Comunes de Uso**

  - **Obtener datos del servidor más rápido** en configuraciones con respaldo.
  - **Elegir la primera respuesta de varios puntos finales**, sin importar si algunos fallan.
  - **Optimización de consultas** cuando solo necesitas un resultado exitoso.

### **Ejemplo Básico de Promise.any**

Imagina que tienes tres promesas que representan tareas con diferentes tiempos de espera. `Promise.any` devuelve el resultado de la primera que se complete exitosamente.

```js linenums="1" title="javascript"
const promesa1 = new Promise((_, reject) => setTimeout(() => reject("Error en Promesa 1"), 1000));
const promesa2 = new Promise(resolve => setTimeout(() => resolve("Promesa 2 completada"), 2000));
const promesa3 = new Promise(resolve => setTimeout(() => resolve("Promesa 3 completada"), 3000));

Promise.any([promesa1, promesa2, promesa3])
    .then(resultado => {
        console.log("Resultado exitoso:", resultado);
    })
    .catch(error => {
        console.log("Error en todas las promesas:", error);
    });
```

En el ejemplo anterior **Promise.any** devuelve el resultado de `promesa2` porque es la primera promesa que se completa exitosamente, mientras que el `promesa1` falla y `promesa3` tarda más tiempo.

## **Usando Promise.any en Casos de Respaldo para Servicios Web**

En aplicaciones que dependen de múltiples servidores o APIs, Promise.any es útil para realizar solicitudes simultáneas y aceptar el primer resultado exitoso. Esta técnica mejora el rendimiento y evita bloqueos si algún servicio falla o responde lentamente.

**Ejemplo: Servicio de Respaldo con Promise.any**

Supongamos que tenemos tres servicios de respaldo que proporcionan información del clima. Al usar `Promise.any` obtenemos la respuesta más rápida sin depender de un solo servidor.

```js linenums="1" title="javascript"
function obtenerClimaServidor1() {
    return new Promise((resolve, reject) => {
        setTimeout(() => resolve("Clima desde Servidor 1: Soleado"), 2000);
    });
}

function obtenerClimaServidor2() {
    return new Promise((resolve, reject) => {
        setTimeout(() => reject("Servidor 2: Error de conexión"), 1500);
    });
}

function obtenerClimaServidor3() {
    return new Promise((resolve, reject) => {
        setTimeout(() => resolve("Clima desde Servidor 3: Nublado"), 1000);
    });
}

// Usamos Promise.any para obtener el primer resultado exitoso
Promise.any([obtenerClimaServidor1(), obtenerClimaServidor2(), obtenerClimaServidor3()])
    .then(resultado => console.log("Resultado exitoso:", resultado))
    .catch(error => console.log("Todas las promesas fallaron:", error));
```

En el ejemplo anterior `Promise.any` devuelve el resultado de `obtenerClimaServidor3` porque es el primer servidor en responder exitosamente, mientras que el `Servidor 2` falla y el `Servidor 1` tarda más.

## **Manejando el `AggregateError` con `Promise.any`**

`Promise.any` se rechazará solo si todas las promesas fallan, devolviendo un `AggregateError`. Este error especial permite identificar las razones de los fallos y decidir qué hacer si no se obtiene ningún resultado.

**Ejemplo de Múltiples Errores en Promise.any**

```js linenums="1" title="javascript"
const promesaFallida1 = new Promise((_, reject) => setTimeout(() => reject("Error en Promesa 1"), 1000));
const promesaFallida2 = new Promise((_, reject) => setTimeout(() => reject("Error en Promesa 2"), 2000));

Promise.any([promesaFallida1, promesaFallida2])
    .then(resultado => console.log("Resultado exitoso:", resultado))
    .catch(error => {
        console.log("Todas las promesas fallaron:");
        error.errors.forEach((err, indice) => console.log(`Error ${indice + 1}: ${err}`));
    });
```

Este ejemplo muestra cómo manejar un `AggregateError` cuando todas las promesas fallan. El error proporciona una lista completa de los motivos de fallo para cada promesa.

## **Comparación entre `Promise.any` y `Promise.race`**

  - `Promise.any`: Devuelve la primera promesa que se resuelve con éxito. Se rechaza solo si todas las promesas fallan.
  - `Promise.race`: Devuelve el primer resultado, ya sea una resolución o un rechazo. Es útil cuando necesitas el primer resultado sin importar su éxito o fracaso.

## **Consideraciones al Usar `Promise.any`**

  1. **Útil en Situaciones de Respaldo**: Ideal para obtener datos en configuraciones con redundancia, donde es probable que una fuente falle.
  2. **Recibe un `AggregateError`**: Cuando todas las promesas fallan, maneja `AggregateError` para obtener los detalles de cada error individual.
  3. **Utilidad en Optimización de Tiempos**: Ideal para obtener respuestas rápidas sin esperar a cada promesa.

***

### **Conclusión**

`Promise.any` es una herramienta poderosa en JavaScript para situaciones donde solo necesitas el primer resultado exitoso entre varias promesas, proporcionando una alternativa útil al método `Promise.race` Además que nos permite optimizar el rendimiento y manejar múltiples operaciones de respaldo sin detenerse en errores individuales.

En el siguiente artículo abordaremos el [Manejo de Errores en Promesas en JavaScript](../manejo-errores-en-promesas/)

***

<br>
