---
hide:
  #- navigation
  - toc
---

<link rel="stylesheet" href="../../assets/stylesheets/javascript.css">

# **Manejo de Errores con Async/Await**

El uso de [async y await](../async-await/) ha hecho que trabajar con código asíncrono sea más claro y legible. Sin embargo, para garantizar la robustez de tus aplicaciones, es fundamental implementar un manejo de errores adecuado. Esto incluye capturar excepciones, validar respuestas y liberar recursos correctamente, incluso cuando ocurren fallos.

En este artículo exploraremos cómo manejar errores con `try/catch`, cómo utilizar `finally` para limpiar recursos y cómo implementar buenas prácticas para mantener tu código seguro y fácil de depurar.

## **Captura de errores con try/catch**

Cuando trabajas con `async/await`, los errores en las operaciones asíncronas pueden ser capturados directamente en un bloque `try/catch`. Esto simplifica el manejo de errores al centralizarlos en una sola sección, en lugar de depender de múltiples `.catch()`.

**Ejemplo básico:**

```js linenums="1" title="javascript"
async function obtenerDatos() {
    try {
        const respuesta = await fetch('https://api.example.com/datos');
        if (!respuesta.ok) throw new Error("Error en la solicitud");

        const datos = await respuesta.json();
        return datos;
    } catch (error) {
        return { error: error.message };
    }
}
```

Si ocurre un error en la solicitud HTTP o al procesar los datos, el bloque `catch` lo captura. El error se devuelve como parte del flujo, en lugar de detener el programa.

## **Validación y manejo de errores condicionales**

Es común agregar validaciones específicas para asegurar que los datos obtenidos sean correctos antes de continuar. Esto permite manejar errores específicos de manera más controlada.

**Ejemplo: Validación de Respuesta**

```js linenums="1" title="javascript"
async function obtenerUsuario(id) {
    try {
        const respuesta = await fetch(`https://api.example.com/usuario/${id}`);
        if (!respuesta.ok) throw new Error("Usuario no encontrado");

        const usuario = await respuesta.json();
        return usuario;
    } catch (error) {
        return { error: error.message };
    }
}
```

Aquí se valida que la respuesta HTTP sea satisfactoria (`ok === true`). Si no lo es, se lanza un error personalizado para indicar que el usuario no fue encontrado.

## **Ejecución final con finally**

El bloque `finally` se ejecuta después de `try/catch`, independientemente de si hubo un error o no. Es útil para liberar recursos, cerrar conexiones o ejecutar acciones finales.

```js linenums="1" title="javascript"
async function procesarArchivo() {
    try {
        const archivo = await abrirArchivo('archivo.txt');
        return archivo;
    } catch (error) {
        return { error: error.message };
    } finally {
        cerrarArchivo();
    }
}
```

En este caso, el bloque `finally` asegura que el archivo se cierre, independientemente de si la operación fue exitosa o fallida.

## **Manejo de errores en operaciones paralelas**

Cuando trabajas con múltiples promesas en paralelo usando `Promise.all`, es importante manejar los errores para que una falla no interrumpa todo el flujo.

**Ejemplo de Manejo de Errores en Promesas Paralelas**

```js linenums="1" title="javascript"
async function obtenerDatosParalelo() {
    try {
        const [usuario, pedidos] = await Promise.all([
        fetch('https://api.example.com/usuario/1').then(res => res.json()),
        fetch('https://api.example.com/pedidos/1').then(res => res.json())
        ]);

        return { usuario, pedidos };
    } catch (error) {
        return { error: error.message };
    }
}
```

En este ejemplo, si alguna de las promesas falla, el bloque `catch` captura el error y permite manejarlo sin interrumpir todo el programa.

## **Buenas prácticas en el manejo de errores con async/await**

Implementar buenas prácticas en el manejo de errores con `async/await` ayuda a mantener el código más seguro y fácil de depurar.

  1. **Centraliza la captura de errores**: Usa funciones auxiliares para encapsular bloques try/catch, evitando repetir lógica de manejo de errores.

```js linenums="1" title="javascript"
async function manejarErrores(funcion) {
    try {
        return await funcion();
    } catch (error) {
        return { error: error.message };
    }
}
```

  2. **Valida cada paso**: Agrega verificaciones condicionales en puntos críticos para capturar errores específicos y mejorar la comprensión del flujo.

  3. **Usa `finally` para liberar recursos**: Asegúrate de que recursos como archivos, conexiones de red o memoria sean liberados sin importar el resultado de la operación.

  4. **Maneja errores de operaciones paralelas**: Asegura que los errores en operaciones concurrentes no afecten el flujo general.

  ***

### **Conclusión**

El manejo adecuado de errores en funciones asíncronas es esencial para escribir aplicaciones confiables y robustas. Al usar bloques `try/catch`, implementar validaciones condicionales y aprovechar `finally` para liberar recursos, puedes reducir la probabilidad de fallos inesperados y mejorar la legibilidad del código. Con estas prácticas, estarás mejor preparado para enfrentar los desafíos de la programación asíncrona en JavaScript.

***

<br>
