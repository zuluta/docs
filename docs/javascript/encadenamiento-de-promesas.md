---
hide:
  #- navigation
  - toc
---

<link rel="stylesheet" href="../../assets/stylesheets/javascript.css">

# **Encadenamiento de Promesas**

El encadenamiento de promesas es una técnica que permite ejecutar operaciones asíncronas de manera secuencial, pasando los resultados de una operación a la siguiente. Este enfoque facilita la gestión de flujos asíncronos complejos, evitando el uso de múltiples callbacks anidados (conocido como “Callback Hell”) y haciendo el código más limpio y legible.

En este artículo, aprenderemos cómo funciona el encadenamiento de promesas, cómo implementarlo correctamente, y las buenas prácticas que debes seguir para maximizar su eficacia.

## **¿Qué es el encadenamiento de promesas?**

El encadenamiento de promesas utiliza el método `.then()` para conectar múltiples [operaciones asíncronas](../programacion-asincrona/) . Cada `then()` devuelve una nueva promesa, lo que permite que los resultados de una operación se pasen a la siguiente de manera ordenada.

**Ejemplo Básico de Encadenamiento**

```js linenums="1" title="javascript"
const promesa = new Promise((resolve) => {
    setTimeout(() => {
        resolve(10);
    }, 1000);
});

promesa
    .then((resultado) => {
        console.log("Primer resultado:", resultado);
        return resultado * 2;
    })
    .then((nuevoResultado) => {
        console.log("Segundo resultado:", nuevoResultado);
        return nuevoResultado + 5;
    })
    .then((final) => {
        console.log("Tercer resultado:", final);
    });
```

En el ejemplo anterior cada operación se encadena con `then`, donde el resultado de una promesa se pasa a la siguiente para continuar con el flujo.

### **¿Cómo Funciona el Encadenamiento?**

El método `.then()` siempre devuelve una nueva promesa, lo que permite construir una cadena de operaciones. Si la función pasada a `.then()`:

  - Devuelve un valor: ese valor se envuelve automáticamente en una promesa resuelta.
  - Devuelve otra promesa: el siguiente `.then()` esperará a que esta se resuelva.

## **Casos prácticos en el encadenamiento**

### **Promesa que devuelve un valor directo**

Si el `then` devuelve un valor que no es una promesa, el valor se envuelve automáticamente en una promesa resuelta.

```js linenums="1" title="javascript"
const promesa = new Promise((resolve) => resolve(5));

promesa
    .then((resultado) => resultado * 2)
    .then((doble) => console.log(doble));
```

### **Promesa que devuelve otra promesa**

Si `.then()` devuelve otra promesa, el encadenamiento esperará hasta que esta nueva promesa se resuelva.

```js linenums="1" title="javascript"
const promesa = new Promise((resolve) => resolve(10));

promesa
    .then((resultado) => {
        return new Promise((resolve) => {
        setTimeout(() => resolve(resultado * 3), 2000);
        });
    })
    .then((resultado) => console.log("Resultado:", resultado)); // (tras 2 segundos)
```

## **Errores comunes en el encadenamiento**

No devolver un valor en `.then()`: Es importante entender que para que el encadenamiento sea efectivo, el `then` debe devolver un valor o una promesa. Si solo se llama al `then` sin devolver nada, la cadena se interrumpe.

```js linenums="1" title="javascript"
const promesa = new Promise((resolve) => resolve(10));

promesa
    .then((resultado) => {
        console.log(resultado); // 10
        // No devuelve nada, el siguiente `.then()` no recibe un valor
    })
    .then((resultado) => {
        console.log("Este código no recibirá un valor adecuado");
    });
```

Asegúrate de devolver un valor o una promesa.

Múltiples `.then()` independientes: Si llamas a `.then()` varias veces sobre la misma promesa sin pasar valores entre ellas, estas ejecuciones no estarán encadenadas.

```js linenums="1" title="javascript"
const promesa = new Promise((resolve) => resolve(10));

promesa
    .then((resultado) => console.log("Primera operación:", resultado)) // Primera operación: 10
    .then((resultado) => console.log("Segunda operación:", resultado)); // Segunda operación: undefined
```

## **Buenas prácticas para el encadenamiento de promesas**

Para aprovechar al máximo el encadenamiento de promesas, ten en cuenta las siguientes recomendaciones:

  1. **Devuelve siempre un valor o promesa en `.then()`**: Asegúrate de devolver algo para que el flujo continúe.
  2. **Evita anidar promesas dentro de `.then()`**: En lugar de anidar, aprovecha el encadenamiento natural.
  3. **Maneja los errores con `.catch()`**: Captura errores en cualquier punto de la cadena para evitar comportamientos inesperados.
  4. **Usa `.finally()` para tareas finales**: Realiza acciones que no dependan del resultado de las promesas.

***

### **Conclusión**

El encadenamiento de promesas en JavaScript es una técnica poderosa para manejar flujos asíncronos de manera ordenada y legible. Al devolver valores o promesas en cada `.then()`, puedes construir cadenas claras y evitar el caos de los callbacks anidados. Además, el uso adecuado de `.catch()` y `.finally()` asegura que tu código sea robusto y fácil de mantener.

En el próximo artículo, exploraremos [Promise.all en JavaScript](../metodo-promise-all/), una herramienta para ejecutar múltiples promesas en paralelo.

***

<br>
