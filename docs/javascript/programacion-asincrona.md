---
hide:
  #- navigation
  - toc
---

<link rel="stylesheet" href="../../assets/stylesheets/javascript.css">

# **Introducción a la Programación Asíncrona**

La programación asíncrona es una técnica que permite que los programas realicen múltiples tareas de manera concurrente, sin bloquear la ejecución del código. En JavaScript, la programación asíncrona es especialmente importante debido a la naturaleza de su entorno, donde muchas operaciones como solicitudes de red, acceso a bases de datos y temporizadores, son inherentemente asíncronas.

En este artículo exploraremos qué es la programación asíncrona, por qué es necesaria en JavaScript y los diferentes enfoques para manejarla.

## **¿Qué es la Programación Asíncrona?**

La programación asíncrona permite ejecutar tareas en paralelo o de manera concurrente sin bloquear el flujo principal del programa. A diferencia de la programación síncrona, donde cada tarea debe completarse antes de pasar a la siguiente, la programación asíncrona permite que otras tareas se ejecuten mientras una operación espera una respuesta.

### **Programación Síncrona vs. Asíncrona**

  - **Síncrona**: El código se ejecuta línea por línea. Si una operación tarda en completarse, bloquea el flujo hasta que termina.
  - **Asíncrona**: Permite que el código siga ejecutándose mientras una operación a largo plazo (como una solicitud HTTP) se resuelve.

**Ejemplo de Comportamiento Síncrono**

```js linenums="1" title="javascript"
console.log("Inicio");

function tareaLarga() {
    // Simula una operación que tarda en completarse
    for (let i = 0; i < 1e9; i++) {}
        console.log("Tarea Larga Completada");
}

tareaLarga();

console.log("Fin");
```

En el ejemplo anterior la ejecución de la función `tareaLarga` bloquea el flujo del programa, haciendo que la línea `console.log("Fin")` no se ejecute hasta que la tarea termine.

***

## **¿Por qué es Necesaria la Programación Asíncrona en JavaScript?**

JavaScript es un lenguaje de un solo hilo, lo que significa que solo puede ejecutar una tarea a la vez. Sin programación asíncrona, cualquier operación que tome mucho tiempo, como una solicitud de red o la lectura de un archivo bloquearía la ejecución del resto del código. Esto haría que la aplicación se sienta lenta o incluso no responda.

**Ejemplos de Casos que Requieren Programación Asíncrona**

  **Solicitudes HTTP**: Realizar llamadas a APIs o cargar datos de un servidor.
  **Operaciones con archivos**: Leer o escribir archivos en sistemas locales o en servidores.
  **Temporizadores**: Ejecuciones diferidas o periódicas con `setTimeout` o `setInterval`.
  **Acceso a bases de datos**: Operaciones de lectura o escritura en bases de datos que pueden tomar tiempo.

Al manejar estas operaciones de manera asíncrona, se mejora la experiencia del usuario al permitir que la interfaz continúe respondiendo mientras se completan las tareas de fondo.

## **Enfoques para la Programación Asíncrona en JavaScript**

JavaScript ofrece diferentes formas para manejar la programación asíncrona, que han evolucionado con el tiempo. Los enfoques más comunes incluyen:

### **1. Callbacks**

[Los callbacks](../funciones-de-callback/) son funciones que se pasan como argumento a otra función y se ejecutan después de que la operación asíncrona se haya completado. Estas fueron el primer enfoque utilizado en JavaScript para manejar la asincronía.

```js linenums="1" title="javascript"
function hacerAlgo(callback) {
    console.log("Comenzando tarea...");
    setTimeout(() => {
        console.log("Tarea completada");
        callback();
    }, 2000);
}

hacerAlgo(() => {
    console.log("Callback ejecutado después de la tarea");
});
```

El problema con los callbacks es que pueden llevar al “Callback Hell” cuando hay múltiples operaciones anidadas.

### **2. Promesas**

Las promesas son objetos que representan la eventual finalización (o falla) de una operación asíncrona y su valor resultante. Fueron introducidas en ES6 para mejorar el manejo de la asincronía y evitar la anidación excesiva de callbacks.

```js linenums="1" title="javascript"
let promesa = new Promise((resolve, reject) => {
    let exito = true;
    
    if (exito) {
        resolve("Operación exitosa");
    } else {
        reject("Ocurrió un error");
    }
});

promesa
    .then(resultado => console.log(resultado))
    .catch(error => console.log(error));
```

### **3. Async/Await**

Async/Await es una sintaxis introducida en ES8 que permite escribir código asíncrono de manera más clara y estructurada, similar al código síncrono. Está basado en promesas, pero hace que el manejo de la asincronía sea más fácil de entender.

```js linenums="1" title="javascript"
async function tareaAsincrona() {
    try {
        let resultado = await new Promise(resolve => setTimeout(() => resolve("Operación exitosa"), 2000));
        console.log(resultado);
    } catch (error) {
        console.log(error);
    }
}

tareaAsincrona();
```

El uso de `async/await` simplifica el manejo de errores y la lectura del flujo asíncrono.

## **El Event Loop en JavaScript**

El Event Loop es un mecanismo que maneja la ejecución de código asíncrono en JavaScript. Permite que el código continúe ejecutándose mientras se completan las tareas asíncronas. Funciona mediante una cola de tareas, donde se agregan las operaciones asíncronas, y las ejecuta una vez que el stack de llamadas está vacío.

### **Cómo Funciona el Event Loop**

  1. **Stack de Llamadas**: Contiene las funciones que están en ejecución.
  2. **Cola de Tareas**: Contiene las operaciones asíncronas que están esperando para ser ejecutadas.
  3. **Event Loop**: Supervisa el stack y la cola, ejecutando las tareas pendientes cuando el stack está vacío.

***

### **Conclusión**

La **programación asíncrona en JavaScript** es esencial para desarrollar aplicaciones eficientes y responsivas. Permite que el código maneje operaciones largas sin bloquear el flujo principal lo que mejora la experiencia del usuario. En esta sección, profundizaremos en temas como promesas, async/await y técnicas avanzadas para gestionar la asincronía.

En el próximo artículo, exploraremos las [promesas en JavaScript](../promesas/), qué son y cómo usarlas para manejar la programación asíncrona.

***
<br>
