---
hide:
  #- navigation
  - toc
---

<link rel="stylesheet" href="../../assets/stylesheets/javascript.css">

# **Generadores Asíncronos**

Los generadores asíncronos en JavaScript permiten producir y consumir valores de manera asíncrona, haciendo uso de promesas para manejar la producción de datos que llegan en tiempos irregulares. Con la ayuda de `async function*` y `for await...of`, los generadores asíncronos facilitan el control de secuencias de datos asíncronas, ideal para leer datos de APIs, streams o cualquier fuente de datos que no esté disponible de inmediato.

## **¿Qué es un Generador Asíncrono?**

Un **generador asíncrono** es similar a un [generador regular](../generadores/), pero permite pausar su ejecución y esperar a que una promesa se resuelva antes de continuar. Esto permite que el generador asíncrono funcione en contextos donde los datos se obtienen en tiempo real o de fuentes asíncronas.

**Sintaxis Básica de un Generador Asíncrono**

Para definir un generador asíncrono, usamos `async function*`:

```js linenums="1" title="javascript"
async function* nombreDelGenerador() {
    // Código del generador asíncrono
}
```

La palabra clave `async` permite que la función pause en `await` dentro de la función generadora, mientras que `*` indica que es un generador.

## **Uso de `yield` y `await` en Generadores Asíncronos**

En un generador asíncrono podemos utilizar `await` para esperar la resolución de promesas antes de pasar al siguiente `yield`. Esto es ideal para manejar datos que tardan en llegar, como resultados de una API o respuestas de una base de datos.

**Ejemplo Básico de un Generador Asíncrono**

```js linenums="1" title="javascript"
async function* generadorAsincrono() {
    const datos = [1, 2, 3];
    for (const dato of datos) {
        await new Promise(resolve => setTimeout(resolve, 1000));  // Espera de 1 segundo
        yield dato;
    }
}

(async () => {
    for await (const valor of generadorAsincrono()) {
        return valor;  // Output: 1, 2, 3 (con un segundo de intervalo)
    }
})();
```

En el código anterior la función generadora `generadorAsincrono` pausa un segundo antes de devolver cada valor, simulando la espera de datos asíncronos en cada paso.

## **Casos de Uso de los Generadores Asíncronos**

Los generadores asíncronos son útiles en situaciones en las que los datos llegan en diferentes intervalos de tiempo o donde la fuente de datos es remota. Algunos casos de uso incluyen:

  - **Procesamiento de Streams de Datos**: Como leer un archivo grande o datos de un stream en red.
  - **Consultas Paginadas en APIs**: Obtener datos en lotes desde un servidor sin bloquear el flujo.
  - **Monitoreo de Eventos en Tiempo Real**: Manejar datos que llegan de manera continua, como notificaciones o mensajes de una aplicación de chat.

**Ejemplo: Generador Asíncrono para Consultas Paginadas**

```js linenums="1" title="javascript"
async function* obtenerDatosPorPagina() {
    let pagina = 1;
    while (true) {
        const respuesta = await fetch(`https://api.example.com/data?page=${pagina}`);
        const datos = await respuesta.json();
        if (datos.length === 0) break;
        yield datos;
        pagina++;
    }
}

(async () => {
    for await (const lote of obtenerDatosPorPagina()) {
        return lote;
    }
})();
```

En este ejemplo `obtenerDatosPorPagina` es un generador asíncrono que recupera y devuelve datos en lotes. El bucle `for await...of` permite procesar cada lote de datos tan pronto como está disponible, sin esperar a que se descargue todo.

## **Ejemplo de Generador Asíncrono con Streams de Datos**

El siguiente ejemplo demuestra cómo usar un generador asíncrono para procesar un stream de datos en fragmentos. Este método es útil para manejar archivos o datos de red grandes.

```js linenums="1" title="javascript"
async function* procesarStream(lectura) {
    const decodificador = new TextDecoderStream();
    const stream = lectura.pipeThrough(decodificador);
    const lector = stream.getReader();

    try {
        while (true) {
            const { done, value } = await lector.read();
            if (done) break;
            yield value;
        }
    } finally {
        lector.releaseLock();
    }
}

// Ejemplo de uso con un objeto de lectura de archivo
(async () => {
    const respuesta = await fetch("https://example.com/archivoGrande.txt");
    for await (const fragmento of procesarStream(respuesta.body)) {
        console.log(fragmento);  // Output: Fragmentos de texto del archivo
    }
})();
```

En el codigo anterior el generador `procesarStream` se encarga de leer fragmentos de un stream de datos en texto. Con `for await...of`, el archivo se procesa en trozos, ideal para manejar datos de gran tamaño sin saturar la memoria.

## **Buenas Prácticas al Usar Generadores Asíncronos**

  1. **Usa Generadores Asíncronos para Fuentes de Datos que Llevan Tiempo**: Aprovecha los generadores asíncronos para obtener datos que pueden tardar en llegar, como API remotas o streams de red.
  2. **Controla la Finalización con `try...finally`**: En generadores que procesan streams o conexiones, usa `try...finally` para liberar recursos como lectores o cierres de streams.
  3. **Utiliza `for await...of` para una Iteración Limpia y Eficiente**: Al iterar con `for await...of`, se puede manejar cada valor asíncrono a medida que está disponible, sin bloquear el flujo del programa.

***

### **Conclusión**

Los generadores asíncronos en JavaScript son herramientas esenciales para trabajar con flujos de datos que se producen de manera asíncrona y controlada. Usando `async function*`, `await` y `for await...of`, es posible procesar datos de APIs, streams y otros recursos remotos sin bloquear la aplicación. Al dominar los generadores asíncronos, puedes construir aplicaciones más eficientes y receptivas para operaciones complejas y en tiempo real.

***

<br>
