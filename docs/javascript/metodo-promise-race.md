---
hide:
  #- navigation
  - toc
---

<link rel="stylesheet" href="../../assets/stylesheets/javascript.css">

# **Promise.race: Resolviendo la Promesa Más Rápida**

El método `Promise.race` en JavaScript permite manejar varias promesas ejecutadas en paralelo y obtener el resultado de la primera que se resuelva o rechace. A diferencia de [Promise.all](../metodo-promise-all/), que espera a que todas las promesas terminen, `.race` devuelve una nueva promesa que se completa tan pronto como una de las promesas originales haya finalizado.

Este método es ideal en situaciones donde la velocidad es esencial, como establecer límites de tiempo para tareas o elegir la respuesta más rápida entre varias fuentes.

## **Cómo funciona Promise.race**

Este método toma un array de promesas como argumento y devuelve una promesa que se resuelve o rechaza dependiendo del estado de la primera promesa en completarse.

**sintaxis básica:**

```js linenums="1" title="javascript"
Promise.race([promesa1, promesa2, promesa3])
    .then(resultado => {
        // Manejar el primer resultado exitoso
    })
    .catch(error => {
        // Manejar el error de la primera promesa rechazada
    });
```

La sintaxis básica es similar a la de otros métodos de promesas. Toma un array de promesas y devuelve una promesa que se resuelve o rechaza tan pronto como cualquiera de las promesas en el array se complete.

### **Ejemplo Básico: Obteniendo el Primer Resultado**

Imaginemos tres promesas con diferentes tiempos de espera. `Promise.race` devolverá el resultado de la promesa que termine primero.

```js linenums="1" title="javascript"
const promesa1 = new Promise(resolve => setTimeout(() => resolve("Promesa 1 completada"), 3000));
const promesa2 = new Promise(resolve => setTimeout(() => resolve("Promesa 2 completada"), 2000));
const promesa3 = new Promise(resolve => setTimeout(() => resolve("Promesa 3 completada"), 1000));

Promise.race([promesa1, promesa2, promesa3])
    .then(resultado => console.log("Resultado:", resultado)) // "Promesa 3 completada"
    .catch(error => console.log("Error:", error));
```

En este ejemplo, aunque las otras promesas aún están en ejecución, así que el método devuelve el resultado de la tercera promesa porque es la más rápida.

## **Usos comunes de Promise.race**

  1. **Establecer un límite de tiempo para operaciones asíncronas**: Puedes crear una promesa que se rechace después de cierto tiempo, sirviendo como un límite para otra operación.

```js linenums="1" title="javascript"
function solicitudConLimiteDeTiempo(promesa, tiempoLimite) {
    const limite = new Promise((_, reject) => 
        setTimeout(() => reject("Tiempo límite alcanzado"), tiempoLimite)
    );
    return Promise.race([promesa, limite]);
}

const solicitud = new Promise(resolve => setTimeout(() => resolve("Solicitud completada"), 3000));

solicitudConLimiteDeTiempo(solicitud, 2000)
    .then(resultado => console.log("Resultado:", resultado))
    .catch(error => console.log("Error:", error)); // "Error: Tiempo límite alcanzado"
```

  2. **Obtener la respuesta más rápida de múltiples solicitudes**: Si haces solicitudes a varias fuentes y solo necesitas la primera respuesta, `race` es una excelente opción.

  3. **Implementar tareas de respaldo**: En caso de que una tarea primaria falle o tarde demasiado, puedes proporcionar una tarea de respaldo más rápida.

## **Manejo de errores en Promise.race**

Cuando la primera promesa en completarse es rechazada, Promise.race devuelve el motivo del error. Las demás promesas no afectan el resultado.

```js linenums="1" title="javascript"
const promesaExitosa = new Promise(resolve => setTimeout(() => resolve("Éxito"), 3000));
const promesaFallida = new Promise((_, reject) => setTimeout(() => reject("Error en promesa"), 1000));

Promise.race([promesaExitosa, promesaFallida])
    .then(resultado => console.log("Resultado:", resultado))
    .catch(error => console.log("Error capturado:", error)); // "Error capturado: Error en promesa"
```

En el código anterior `Promise.race` captura el error de `promesaFallida` porque es la que termina primero.

## **Limitando el Tiempo de Ejecución de una Promesa con `Promise.race`**

Uno de los usos más comunes de `Promise.race` es establecer un tiempo límite para una operación asíncrona. En este caso creamos una promesa que se rechaza después de un tiempo específico para que este método pueda usarla como límite de tiempo.

**Ejemplo: Límite de Tiempo para una Solicitud**

```js linenums="1" title="javascript"
function solicitudConLimiteDeTiempo(promesa, tiempoLimite) {
    let limite = new Promise((_, reject) =>
        setTimeout(() => reject("Tiempo límite alcanzado"), tiempoLimite)
    );

    return Promise.race([promesa, limite]);
}

let solicitud = new Promise(resolve => setTimeout(() => resolve("Solicitud completada"), 3000));

solicitudConLimiteDeTiempo(solicitud, 2000)
    .then(resultado => console.log(resultado))
    .catch(error => console.log("Error:", error));
```

En el ejemplo anterior, si la promesa de `solicitud` tarda más de 2000 ms en completarse, el metodo devuelve el error “Tiempo límite alcanzado”.

## **Consideraciones importantes al usar Promise.race**

  1. **Primer resultado o error**: `Promise.race` no garantiza que todas las promesas se completen, solo devuelve el resultado de la primera que lo haga.
  2. **Usar con límites de tiempo**: Es excelente para limitar la duración de una tarea, rechazando las promesas que tarden demasiado.
  3. **Ignorar las promesas restantes**: Las promesas que terminan después de la primera ya no afectan el resultado. Esto puede ser útil en algunos casos, pero también puede generar operaciones innecesarias en segundo plano.


***

### **Conclusión**

El método `Promise.race` es una herramienta poderosa en JavaScript que permite optimizar el manejo de operaciones asíncronas donde la velocidad es clave. Ya sea para limitar tiempos de espera, obtener la respuesta más rápida o manejar tareas de respaldo, este método simplifica y agiliza el flujo de trabajo en aplicaciones modernas.

En el siguiente artículo, exploraremos [Promise.allSettled](../metodo-promise-allsettled/), una alternativa que devuelve el estado de todas las promesas, sin importar si fueron resueltas o rechazadas.

***

<br>
