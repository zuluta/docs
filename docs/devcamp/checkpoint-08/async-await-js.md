---
hide:
  #- navigation
  #- toc
---

La introducción de async/await en JavaScript transformó la manera de manejar el código asíncrono, haciéndolo más legible y fácil de seguir. Estas palabras clave permiten trabajar con promesas de forma más fluida, logrando que el código se parezca al flujo síncrono. Esto no solo mejora la comprensión del código, sino que también facilita su depuración.

En este artículo, aprenderemos cómo funcionan `async` y `await`, sus ventajas, y cómo usarlos para simplificar operaciones asíncronas complejas.

## **¿Qué son async y await?**

`async` y `await` son palabras clave introducidas en **ES2017** que permiten manejar código asíncrono de manera más clara. Estas herramientas convierten el trabajo con promesas en un proceso más lineal, facilitando la escritura y lectura del código.

  - **async**: Convierte automáticamente una función utilitaria en una función asíncrona que devuelve una promesa.
  - **await**: Pausa la ejecución de una función `async` hasta que la promesa asociada sea resuelta o rechazada.

**Ejemplo básico de una función async:**

```js linenums="1" title="javascript"
async function saludo() {
    return "Hola, Async/Await";
}

saludo().then(mensaje => console.log(mensaje));
```

Al usar `async`, la función `saludo` devuelve automáticamente una promesa.El valor `"Hola, Async/Await"` se convierte en el resultado de la promesa.

**Uso de await para manejar promesas:**

La palabra clave `await` permite pausar la ejecución de una función `async` hasta que la promesa asociada se resuelva. Esto elimina la necesidad de usar `.then()` para manejar resultados, logrando un flujo más natural.

**Ejemplo básico de await:**

```js linenums="1" title="javascript"
async function obtenerDatos() {
    const respuesta = await fetch('https://api.example.com/datos');
    const datos = await respuesta.json();
    return datos;
}
```

La función `fetch` devuelve una promesa. `await` espera a que esta se resuelva. El flujo no continúa hasta que se obtienen y procesan los datos.

## **Ejecución secuencial con async/await**

`async/await` también permite ejecutar operaciones de manera secuencial, en caso de que cada tarea dependa de la finalización de la anterior. Esta secuencia asegura que el flujo de datos sea correcto y elimina la necesidad de anidar múltiples `.then()` en una cadena.

**Ejemplo de Ejecución Secuencial:**

```js linenums="1" title="javascript"
async function procesoSecuencial() {
    const paso1 = await Promise.resolve("Paso 1 completado");
    console.log(paso1);

    const paso2 = await Promise.resolve("Paso 2 completado");
    console.log(paso2);

    const paso3 = await Promise.resolve("Paso 3 completado");
    console.log(paso3);
}

procesoSecuencial();
```

En el ejemplo anterior, cada `await` asegura que el paso anterior esté completo antes de continuar. Esta función asíncrona produce lo que sería una cadena de promesas en un flujo de código fácil de entender y sin necesidad de anidación.

## **Ejecución paralela con Promise.all y async/await**

Aunque `async/await` es ideal para flujos secuenciales, también puedes usarlo con `Promise.all` para ejecutar tareas en paralelo. Esto mejora el rendimiento en operaciones independientes.

**Ejemplo de Ejecución Paralela:**

```js linenums="1" title="javascript"
async function obtenerDatosParalelo() {
    try {
        const [usuario, pedidos] = await Promise.all([
        fetch('https://api.example.com/usuario/1').then(res => res.json()),
        fetch('https://api.example.com/pedidos/1').then(res => res.json())
        ]);

        return { usuario, pedidos }; // Devuelve ambos resultados como un objeto
    } catch (error) {
        return { error: error.message }; // Devuelve el error capturado
    }
}

obtenerDatosParalelo().then(resultado => {
    // Manejo de resultado o error
});

```

En el ejemplo anterior las dos solicitudes se ejecutan en paralelo. `Promise.all` espera a que ambas operaciones finalicen, pero sin depender una de la otra, mejorando el rendimiento de la aplicación.

## **Manejo de errores con try/catch**

El manejo de errores es más limpio con `try/catch` dentro de funciones `async`, ya que centraliza la gestión de errores en un solo bloque. Esto asegura que todos los errores de la función `async` se gestionen en un solo bloque.

**Ejemplo de manejo de errores:**

```js linenums="1" title="javascript"
async function obtenerDatosSeguro() {
    try {
        const respuesta = await fetch('https://api.example.com/datos');
        if (!respuesta.ok) throw new Error("Error en la solicitud");

        const datos = await respuesta.json();
        return datos; // Devuelve los datos obtenidos
    } catch (error) {
        return { error: error.message }; // Devuelve el error capturado
    }
}

obtenerDatosSeguro().then(resultado => {
    // Manejo de resultado o error
});

```

`try` protege el bloque donde pueden ocurrir errores. `catch` captura y maneja cualquier error, como fallos de red o datos inválidos.

## **Buenas prácticas con async/await**

Para aprovechar al máximo `async/await`, es importante tener en cuenta algunas buenas prácticas que aseguran un manejo eficiente y ordenado de las operaciones asíncronas.

  1. **Usa `Promise.all` para operaciones paralelas**: Cuando varias tareas no dependen unas de otras, ejecútalas simultáneamente para mejorar el rendimiento.
  2. **Utiliza `try/catch` para capturar errores**: Centraliza el manejo de errores para evitar fallos inesperados y mejorar la depuración.
  3. **Evita bloqueos innecesarios**: No uses `await` en operaciones que no necesitan ser pausadas. Esto puede ralentizar el flujo del programa.
  4. **Manejo eficiente de errores**: En flujos complejos, combina `try/catch` con funciones reutilizables para reducir la redundancia.

***

### **Conclusión**

`async` y `await` han revolucionado la forma de manejar la asincronía en JavaScript, haciendo que el código sea más limpio, legible y fácil de mantener. Al comprender su funcionamiento y seguir buenas prácticas, puedes optimizar tus aplicaciones y simplificar el desarrollo de tareas asíncronas.

En el próximo artículo, exploraremos cómo [manejar errores con async/await](../manejo-de-errores-async-await/), asegurando que tu código sea robusto y eficiente.

***

<br>
