---
hide:
  #- navigation
  - toc
---

<link rel="stylesheet" href="../../assets/stylesheets/javascript.css">

# **Iteradores Asíncronos**

Con el auge de aplicaciones que manejan datos en tiempo real y operaciones asíncronas como la consulta a APIs o la lectura de streams, los iteradores asíncronos se han vuelto una herramienta fundamental en JavaScript. Estos iteradores permiten manejar secuencias de datos que no están disponibles de inmediato, de una manera controlada y eficiente.

En este artículo exploraremos qué son los iteradores asíncronos, cómo funcionan, sus casos de uso, además de prácticas para utilizarlos en proyectos modernos.

## **¿Qué es un iterador asíncrono?**

Un iterador asíncrono es un objeto que sigue el protocolo de iteración asíncrona, devolviendo una secuencia de promesas en lugar de valores inmediatos. Cada llamada al método `next()` devuelve una promesa que se resuelve cuando el valor está disponible, lo que permite manejar datos que llegan de forma intermitente o tardía.

**Ejemplo básico:**

Para crear un iterador asíncrono, debes implementar el método `Symbol.asyncIterator`. Este método devuelve un objeto que contiene un método `next()` que devuelve una promesa.

```js linenums="1" title="javascript"
const objetoAsincrono = {
    [Symbol.asyncIterator]() {
        let i = 0;
        return {
            next() {
                if (i < 5) {
                    return new Promise(resolve => {
                        setTimeout(() => resolve({ value: i++, done: false }), 1000);
                    });
                } else {
                    return Promise.resolve({ done: true });
                }
            }
        };
    }
};
```

En este ejemplo: Una vez completados los valores, devuelve `{ done: true }`. El iterador simula una secuencia de datos donde cada valor se produce después de un segundo.

## **Iteración asíncrona con for await…of**

JavaScript introdujo el bucle `for await...of` para iterar sobre objetos asíncronos de forma secuencial. Este bucle espera a que cada promesa en la secuencia se resuelva antes de proceder al siguiente valor.

```js linenums="1" title="javascript"
async function procesarDatos() {
    for await (const valor of objetoAsincrono) {
        console.log(valor);
    }
}

procesarDatos();
```

En este ejemplo, `for await...of` espera que cada `next()` devuelva un valor antes de continuar, lo que permite manejar datos asincrónicos de forma secuencial sin necesidad de múltiples promesas encadenadas.

## **Casos de uso de iteradores asíncronos**

Los iteradores asíncronos son ideales en situaciones donde los datos no están disponibles inmediatamente o se reciben de forma fragmentada:

  1. **Lectura de streams de datos**: Procesar archivos grandes o streams de red en fragmentos a medida que llegan.
  2. **Consulta de APIs paginadas**: Iterar sobre resultados de una API que devuelve datos en lotes.
  3. **Monitoreo de eventos en tiempo real**: Procesar entradas continuas, como datos de sensores o mensajes de chat.

**Ejemplo: Iteración sobre una Fuente de Datos Remota**

Imaginemos que estamos solicitando datos a una API que devuelve resultados en lotes. Usar un iterador asíncrono nos permite procesar cada lote tan pronto como esté disponible.

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

async function procesarDatos() {
    for await (const datos of obtenerDatosPorPagina()) {
        return datos;
    }
}

procesarDatos();
```

En el ejemplo anterior `obtenerDatosPorPagina` es un generador asíncrono que obtiene y devuelve lotes de datos de la API. Con `for await...of`, podemos procesar cada lote sin esperar que se complete toda la descarga.

## **Implementación de iteradores asíncronos personalizados**

Podemos implementar iteradores asíncronos personalizados en nuestros propios objetos, lo hacemos usando `Symbol.asyncIterator`. Esto permite crear estructuras de datos que solo proporcionan un valor cuando está disponible.

**Ejemplo de un Iterador Asíncrono Personalizado**

```js linenums="1" title="javascript"
const generadorAsincrono = {
    [Symbol.asyncIterator]() {
        let contador = 1;
        return {
            async next() {
                if (contador <= 5) {
                    await new Promise(resolve => setTimeout(resolve, 1000));
                    return { value: contador++, done: false };
                } else {
                    return { done: true };
                }
            }
        };
    }
};

async function ejecutarIterador() {
    for await (const valor of generadorAsincrono) {
        return valor;
    }
}

ejecutarIterador();
```

En este caso, `generadorAsincrono` es un iterador que produce valores cada segundo. El bucle `for await...of` permite iterar sobre esos valores en orden, esperando cada uno hasta que esté disponible.

## **Buenas prácticas al usar iteradores asíncronos**

  1. **Controla el flujo con `for await...of`**: Este bucle es la forma más limpia y legible de manejar iteradores asíncronos.
  2. **Evita iteradores infinitos sin control**: Si tu iterador asíncrono no tiene un límite claro, implementa un mecanismo de cancelación para evitar consumir recursos innecesarios.
  3. **Usa `try...catch` para manejar errores**: Los iteradores asíncronos pueden fallar debido a problemas de red o datos, por lo que es importante manejar los errores adecuadamente.

***

### **Conclusión**

Los iteradores asíncronos son una herramienta poderosa para manejar flujos de datos que no están disponibles de inmediato. Ya sea para procesar streams, consultar APIs paginadas o monitorear eventos en tiempo real, los iteradores asíncronos ofrecen una solución eficiente y estructurada para manejar datos asíncronos en JavaScript.

En el próximo artículo, exploraremos los [Generadores Asíncronos](../generadores-asincronos/), una extensión que combina la flexibilidad de los generadores con el poder de la asincronía.

***

<br>
