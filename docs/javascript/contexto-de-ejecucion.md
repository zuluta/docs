---
hide:
  #- navigation
  - toc
---

<link rel="stylesheet" href="../../assets/stylesheets/javascript.css">

# **Contexto de Ejecución**

El contexto de ejecución es uno de los conceptos clave para entender cómo JavaScript procesa y ejecuta el código. Todo lo que ocurre en JavaScript, desde la ejecución de una línea de código hasta la llamada de una función, ocurre dentro de un contexto de ejecución.

En este artículo exploraremos qué es el contexto de ejecución, sus fases principales (creación y ejecución), y cómo afecta al comportamiento de tu código.

## **¿Qué es el Contexto de Ejecución?**

Cuando el motor de JavaScript ejecuta el código crea un espacio llamado **contexto de ejecución**. Este espacio es el entorno donde se evalúan y ejecutan las instrucciones del programa. Existen dos tipos principales:

  1. **Contexto de ejecución global**: Es el entorno base que se crea cuando el código comienza a ejecutarse.
  2. **Contexto de ejecución de función**: Se crea cada vez que se invoca una función.

```js linenums="1" title="javascript"
let x = 10;

function timesTen(a) {
    return a * 10;
}

let y = timesTen(x);

console.log(y);
```

En el ejemplo anterior pasa lo siguiente:

  1. Se declara la variable `x` y se inicializa con el valor `10`.
  2. Se define la función `timesTen` que toma un argumento y lo multiplica por `10`.
  3. Se llama a `timesTen` con el valor de `x` y el resultado se almacena en `y`.
  4. Finalmente, se imprime el valor de `y`.

Detrás de escena, el motor de JavaScript crea y gestiona diferentes contextos de ejecución para llevar a cabo estas acciones.

## **Fases del Contexto de Ejecución**

Cada contexto de ejecución tiene dos fases principales:

### 1. **Fase de Creación**

En esta fase, el motor de JavaScript prepara todo lo necesario para ejecutar el código. Esto incluye:

  - **Crear el objeto global**: En el navegador, esto es `window`, mientras que en Node.js es `global`.
  - **Crear el objeto `this`**: En el contexto global, `this` se enlaza al objeto global.
  - **Configurar el espacio de memoria**: El motor establece un área para almacenar variables y referencias a funciones.
  - **Inicializar variables y funciones**: Las variables se inicializan con el valor `undefined`, y las declaraciones de funciones se almacenan completas.

```js linenums="1" title="javascript"
let x = 10;

function timesTen(a) {
    return a * 10;
}

let y;
```

**Durante esta fase**: Se declara `x` y `y`, pero ambas se inicializan como `undefined`. La función `timesTen` se almacena en memoria como una referencia completa.

### 2. **Fase de Ejecución**

En esta fase el motor de JavaScript ejecuta el código línea por línea: Asigna valores a las variables, evalúa expresiones, llama a funciones y gestiona sus contextos de ejecución.

```js linenums="1" title="javascript"
function timesTen(a) {
    return a * 10;
}

let x = 10; // Se asigna 10 a x
let y = timesTen(x); // Llama a timesTen con x como argumento
console.log(y); // Muestra 100 en la consola
```

Cuando se llama a `timesTen`, se crea un nuevo contexto de ejecución de función, donde:

  1. Se crea un objeto `arguments` que referencia los parámetros pasados.
  2. Se inicializa el parámetro `a` con el valor `10`.
  3. Se ejecuta el cuerpo de la función, devolviendo el resultado `100`.

## **El Papel de la Pila de Llamadas (Call Stack)**

El motor de JavaScript utiliza una estructura llamada **call stack** (pila de llamadas) para realizar un seguimiento de los contextos de ejecución. Cada vez que se invoca una función, su contexto de ejecución se agrega a la pila. Una vez que se completa, se elimina de la pila.

**Ejemplo del call stack**: Teniendo en cuenta el código del ejemplo anterior, consideremos la siguiente secuencia:

  1. El contexto global se coloca en la pila.
  2. Cuando se llama a `timesTen`, su contexto de ejecución se apila.
  3. Al finalizar la ejecución de `timesTen`, su contexto se elimina y el control regresa al contexto global.

## **Ejemplo: Múltiples contextos de ejecución**

El contexto de ejecución no se limita a un solo nivel, en un programa real múltiples funciones pueden interactuar y llamarse entre sí. Cada vez que se invoca una función, se crea un nuevo contexto de ejecución que se agrega a la pila de llamadas. En este ejemplo, veremos cómo JavaScript gestiona estos contextos de ejecución y cómo la pila organiza el flujo del programa.

```js linenums="1" title="javascript"
function first() {
    console.log("Primera función");
    second();
}

function second() {
    console.log("Segunda función");
}

console.log("Inicio del programa");
first();
console.log("Fin del programa");
```

En el código anterior pasa lo siguiente:

  1. El programa comienza con el contexto global, donde se ejecuta el primer `console.log`.
  2. Al llamar a `first()`, se crea un nuevo contexto de ejecución y se agrega a la pila.
  3. Dentro de `first`, se invoca `second()`, creando un tercer contexto de ejecución.
  4. Una vez que `second` finaliza, su contexto se elimina de la pila y el control regresa a `first`.
  5. Finalmente, el contexto de `first se elimina y el flujo vuelve al contexto global para completar el programa.

### **Explicación del flujo**

  1. **Contexto global**: Se ejecuta el código principal y se llama a la función `first`.
  2. **Contexto de `first`**: Se registra el mensaje “Primera función” y se llama a la función `second`.
  3. **Contexto de `second`**: Se registra “Segunda función”, y su ejecución se completa.
  4. **Regreso al contexto de `first`**: Se finaliza la ejecución de `first` y se elimina su contexto.
  5. **Regreso al contexto global**: Se imprime “Fin del programa”.

Este flujo muestra cómo JavaScript utiliza la pila de llamadas para gestionar múltiples contextos de ejecución de manera eficiente.

***

### **Conclusión**

El contexto de ejecución es el núcleo de cómo JavaScript procesa el código. Comprender cómo se crean y manejan estos contextos, junto con sus fases, te ayuda a depurar errores, entender el flujo del programa y escribir código más eficiente.

En el próximo artículo exploraremos la [pila de llamadas (call stack)](../call-stack/) en profundidad para entender cómo JavaScript organiza y procesa múltiples contextos de ejecución.

***

<br>
