---
hide:
  #- navigation
  - toc
---

<link rel="stylesheet" href="../../assets/stylesheets/javascript.css">

# **Promesas**

Las promesas en JavaScript son una herramienta esencial para manejar operaciones asíncronas de manera estructurada y predecible. Representan la eventual finalización (o falla) de una operación y permiten escribir código más limpio y mantenible que los callbacks tradicionales.

En este artículo exploraremos qué son las promesas, qué problemas resuelven y cómo se utilizan, con ejemplos prácticos para una comprensión completa.

## **¿Qué es una promesa?**

básicamente, una promesa es un objeto que representa un valor que puede estar disponible en el presente, en el futuro o nunca. Este objeto tiene tres estados posibles:

  1. **Pendiente** (`pending`): La operación aún no ha finalizado.
  2. **Resuelta** (`fulfilled`): La operación se completó con éxito y la promesa tiene un valor resultante.
  3. **Rechazada** (`rejected`): La operación falló y la promesa tiene un motivo de error.

**Ejemplo básico:**

```js linenums="1" title="javascript"
const promesa = new Promise((resolve, reject) => {
    const exito = true;

    if (exito) {
        resolve("Operación exitosa");
    } else {
        reject("Error en la operación");
    }
});
```

  - `resolve(valor)`: Cambia el estado de la promesa a fulfilled y proporciona el resultado.
  - `reject(error)`: Cambia el estado de la promesa a rejected y proporciona un motivo de error.

El estado de una promesa cambia de `pending` a `fulfilled` o `rejected` cuando la operación asíncrona termina y no puede cambiar de nuevo.

## **¿Qué Problemas Resuelven las Promesas?**

Antes de que las promesas fueran introducidas en versión de ES6, la forma principal de manejar la programación asíncrona en JavaScript era mediante callbacks. Aunque estos funcionan, tienen algunas desventajas importantes:

  - **Callback Hell**: Cuando se anidan múltiples callbacks, el código se vuelve difícil de leer y mantener.
  - **Manejo de Errores Complejo**: La gestión de errores en callbacks anidados puede ser complicada.
  - **Invocación de Múltiples Callbacks**: Puede haber errores si un callback se llama varias veces, lo cual es difícil de controlar.

Las promesas resuelven estos problemas al proporcionar una estructura más limpia para manejar las operaciones asíncronas, con un enfoque basado en métodos para manejar el resultado o el error.

## **Creación de una Promesa en JavaScript**

Para crear una promesa en JavaScript, se utiliza el constructor `Promise`, que toma una función ejecutora como argumento. Esta función ejecutora recibe dos parámetros: `resolve` y `reject`, que se utilizan para resolver o rechazar la promesa.

```js linenums="1" title="javascript"
const promesa = new Promise((resolve, reject) => {
    const exito = true;
    
    if (exito) {
        resolve("La operación fue exitosa");
    } else {
        reject("Ocurrió un error en la operación");
    }
});
```

En este ejemplo la promesa se resuelve con `resolve` si la operación tiene éxito o con `reject` si ocurre un error.

### **Métodos principales para manejar una promesa**

Una vez creada una promesa se pueden utilizar los métodos `then` y `catch` para manejar los resultados de la promesa.

### **Manejar la Promesa Resuelta: `then()`**

El método `then()` se utiliza para manejar el valor de una promesa resuelta. Recibe una función que se ejecuta cuando la promesa cambia a `fulfilled`.

```js linenums="1" title="javascript"
promesa.then(resultado => {
    // Operación a ejecutar si la promesa es exitosa
});
```

### **Manejar la Promesa Rechazada: `catch()`**

El método `catch()` se utiliza para manejar errores en la promesa. Recibe una función que se ejecuta cuando la promesa es rechazada.

```js linenums="1" title="javascript"
promesa.catch(error => {
    // Error a ejecutar si la promesa es rechazada
});
```

### **Ejecutar Código Independientemente del Resultado: `finally()`**

El método `finally()` se ejecuta una vez que la promesa ha sido resuelta o rechazada, sin importar el resultado. Es útil para liberar recursos o realizar acciones finales.

```js linenums="1" title="javascript"
promesa.finally(() => {
    // Tarea a ejecutar cuando finaliza la operación
});
```

## **Encadenamiento de Promesas**

Una de las características más potentes de las promesas es su capacidad de encadenar múltiples operaciones asíncronas de manera secuencial.

Una de las características más poderosas de las promesas es la posibilidad de encadenar múltiples operaciones asíncronas. Cada `then()` devuelve una nueva promesa, lo que permite encadenar las operaciones secuencialmente.

**Ejemplo de Encadenamiento:**

```js linenums="1" title="javascript"
const promesaEncadenada = new Promise((resolve, reject) => {
  setTimeout(() => resolve(10), 1000);
});

promesaEncadenada
  .then(resultado => {
    console.log("Resultado inicial:", resultado); // Resultado inicial: 10
    return resultado * 2;
  })
  .then(nuevoResultado => {
    console.log("Doblado:", nuevoResultado); // Doblado: 20
    return nuevoResultado + 5;
  })
  .then(final => {
    console.log("Resultado final:", final); // Resultado final: 25
  })
  .catch(error => {
    console.log("Error:", error);
  })
  .finally(() => {
    console.log("Operación completada, ya sea éxito o error."); // Siempre se ejecuta
  });

```

**Ventajas del encadenamiento:**

  - Hace que el flujo de operaciones sea más claro y lineal.
  - Evita la anidación excesiva.

## **Promesas vs. Callbacks:**

Las promesas ofrecen varias ventajas sobre el uso tradicional de callbacks para manejar operaciones asíncronas:

**Legibilidad:**

  - **Promesas**: Ofrecen una sintaxis más clara, evitando la anidación excesiva que ocurre con los callbacks. Esto hace que el flujo de operaciones sea más fácil de seguir y entender.
  - **Callbacks**: Pueden ser difíciles de leer y mantener, especialmente cuando se anidan múltiples operaciones, lo que lleva al problema conocido como “Callback Hell”.

**Manejo de errores:**

  **Promesas**: Centralizan el manejo de errores con el método .catch(), que captura cualquier fallo en la cadena de operaciones asíncronas, facilitando su gestión.
  **Callbacks**: Requieren manejar los errores manualmente en cada nivel de anidación, lo que incrementa la complejidad del código y la posibilidad de omitir errores.

**Encadenamiento:**

  **Promesas**: Permiten un flujo lineal y predecible mediante el uso de `.then()`, lo que mejora la estructura y claridad del código.
  **Callbacks**: El encadenamiento de operaciones implica anidar callbacks, lo que puede resultar en un código desorganizado y difícil de depurar.

## **Buenas prácticas al usar promesas**

  1. **Siempre maneja los errores**: Usa `.catch()` para capturar cualquier error en la cadena de promesas.
  2. **Usa `finally` para tareas finales**: Útil para liberar recursos o realizar acciones finales independientemente del resultado.
  3. **Evita promesas excesivamente anidadas**: Encadena operaciones en lugar de anidar `.then()`.

```js linenums="1" title="javascript"
promesa
  .then(resultado => {
    // Operación exitosa
  })
  .catch(error => {
    // Manejo de errores
  })
  .finally(() => {
    // Acción final
  });
```

***

### **Conclusión**

Las promesas en JavaScript representan una mejora significativa en el manejo de operaciones asíncronas. Ofrecen una forma clara y estructurada de manejar tareas largas o complejas, haciendo el código más legible y fácil de mantener. Comprender cómo crear, manejar y encadenar promesas es esencial para desarrollar aplicaciones modernas y responsivas.

En el siguiente artículo abordaremos el [encadenamiento de promesas](../encadenamiento-de-promesas/), cómo se puede simplificar el flujo de trabajo y qué técnicas usar para manejar la programación asíncrona de manera efectiva.

***

<br>
