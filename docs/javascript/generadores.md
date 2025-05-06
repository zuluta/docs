---
hide:
  #- navigation
  - toc
---

<link rel="stylesheet" href="../../assets/stylesheets/javascript.css">

# **Generadores**

Los generadores en JavaScript son un tipo especial de función que permite pausar y reanudar su ejecución, devolviendo valores en múltiples etapas. Esta capacidad de “pausa” convierte a los generadores en una herramienta valiosa para manejar secuencias y flujos de datos complejos.

En este artículo exploraremos cómo funcionan los generadores, su sintaxis y el uso de las palabras clave `function*` y `yield`. También revisaremos sus aplicaciones prácticas y las buenas prácticas para aprovechar al máximo esta característica.

## **¿Qué es un generador?**

Un generador es una función que puede detener temporalmente su ejecución y luego reanudarla desde donde se detuvo. Cada vez que un generador se “pausa”, puede devolver un valor sin perder su contexto. Esto se logra mediante la palabra clave `yield`, que suspende la función y espera la siguiente llamada al método `next()` para continuar.

**Sintaxis básica:**

Para definir un generador, utiliza `function*` en lugar de `function`. Esto indica a JavaScript que la función es un generador.

```js linenums="1" title="javascript"
function* saludo() {
    yield "Hola";
    yield "¿Cómo estás?";
    return "¡Adiós!";
}

const generador = saludo();
console.log(generador.next());
console.log(generador.next());
console.log(generador.next());
```

La palabra clave `yield` detiene la ejecución del generador y devuelve un valor. El método `next()` reanuda la ejecución hasta encontrar el siguiente `yield` o el final de la función.

## **Diferencias entre funciones normales y generadores**

Los generadores y las funciones normales comparten la capacidad de encapsular bloques de código reutilizables, pero su funcionamiento y propósito son distintos. Mientras que una función normal sigue un flujo lineal y se ejecuta de principio a fin de una sola vez, los generadores permiten un control incremental sobre la ejecución, ofreciendo pausas y reanudaciones.

### **Funciones normales:**

  - Ejecutan todo su código de una vez, de principio a fin.
  - Devuelven un solo valor con `return`.

### **Generadores:**

  - Pueden pausar su ejecución en cualquier punto usando `yield`.
  - Devuelven múltiples valores a medida que se llama a `next()`.
  - Mantienen su estado entre ejecuciones, recordando variables y contexto.

```js linenums="1" title="javascript"
// Función normal
function saludoNormal() {
    return "Hola";
}

// Generador
function* saludoGenerador() {
    yield "Hola";
    yield "¿Qué tal?";
}

console.log(saludoNormal()); // "Hola"

const generador = saludoGenerador();
console.log(generador.next().value);
console.log(generador.next().value);
```

## **Aplicaciones prácticas de los generadores**

### **Generador de secuencias numéricas**

Los generadores son ideales para manejar secuencias infinitas o series numéricas, permitiendo obtener valores solo cuando son necesarios.

```js linenums="1" title="javascript"
function* generadorDeNumeros() {
    let numero = 1;
    while (true) {
        yield numero++;
    }
}

const secuencia = generadorDeNumeros();
console.log(secuencia.next().value);
console.log(secuencia.next().value);
console.log(secuencia.next().value);
```

Este generador produce una secuencia infinita de números incrementales, útil para generar identificadores únicos o manejar series sin límite.

### **Ejecución condicional y controlada**

Los generadores permiten dividir procesos en pasos controlados, pausando en cada `yield` y reanudando según sea necesario.

```js linenums="1" title="javascript"
function* flujoDeTrabajo() {
    console.log("Iniciando...");
    yield "Paso 1 completo";
    console.log("En el paso 2...");
    yield "Paso 2 completo";
    console.log("Finalizando...");
    return "Trabajo terminado";
}

const proceso = flujoDeTrabajo();

console.log(proceso.next().value);
console.log(proceso.next().value);
console.log(proceso.next().value);
```

En el ejemplo anterior el generador `flujoDeTrabajo` permite ejecutar el proceso en pasos controlados, pausando en cada `yield` y reanudando según sea necesario.

### **Delegación con `yield`***

A veces un generador necesita delegar la iteración a otro generador o iterable. `yield*` permite incluir los valores de otro generador o iterable en la secuencia, de manera que el generador principal actúe como intermediario. Esto es útil para dividir la lógica en generadores más pequeños y combinarlos en uno solo.

```js linenums="1" title="javascript"
function* generadorPrincipal() {
    yield* generadorSecundario();
    // código adicional en el generador principal
}
```

**Ejemplo de yield* con Generadores Anidados**

```js linenums="1" title="javascript"
function* generador1() {
    yield "Primero";
    yield "Segundo";
}

function* generador2() {
    yield "Inicio Generador 2";
    yield* generador1();  // Delegación al generador1
    yield "Fin Generador 2";
}

const iterador = generador2();

console.log(iterador.next().value);
console.log(iterador.next().value);
console.log(iterador.next().value);
console.log(iterador.next().value);
```

En el anterior codigo vemos que `generador2` incluye los valores de `generador1` dentro de su secuencia mediante `yield*`, permitiendo que ambos generadores actúen como una única fuente de valores.

## **Comunicación bidireccional con `next(value)`**

Además de avanzar el generador a la siguiente instrucción `yield`, el método `next()` puede recibir un argumento que se pasa como resultado de la última instrucción `yield`. Esto permite enviar información al generador durante la iteración.

```js linenums="1" title="javascript"
const iterador = generador();
iterador.next(valor);  // Envia el valor al generador
```

**Ejemplo de `next(value)` para Pasar Valores**

```js linenums="1" title="javascript"
function* calculadora() {
    const num1 = yield "Ingresa el primer número:";
    const num2 = yield "Ingresa el segundo número:";
    yield `Resultado: ${num1 + num2}`;
}

const iterador = calculadora();

console.log(iterador.next().value);
console.log(iterador.next(5).value);
console.log(iterador.next(3).value);
```

En el anterior ejemplo `next(5)` y `next(3)` envían los valores `5` y `3` al generador `calculadora`, permitiendo realizar una suma dentro del generador. Esto es útil para construir flujos en los que el generador depende de datos externos en cada paso.

## **Buenas prácticas al usar generadores**

  1. **Maneja grandes secuencias de datos**: Los generadores son ideales para flujos de datos continuos o secuencias infinitas.
  2. **Evita generadores en procesos simples**: Para tareas sencillas, las funciones normales son más eficientes.
  3. **Usa `yield*` para dividir lógica compleja**: Mantén tu código modular delegando operaciones a generadores más pequeños.
  4. **Aprovecha la comunicación bidireccional**: Usa `next(value)` para flujos de datos que dependen de la entrada del usuario.

***

### **Conclusión**

Los generadores en JavaScript son una herramienta poderosa para controlar la ejecución de funciones de manera pausada y secuencial. Con `yield` y `next()`, puedes manejar secuencias de datos grandes, gestionar procesos paso a paso y optimizar el uso de memoria. Comprender cómo funcionan y cómo aplicarlos te permitirá mejorar la eficiencia y flexibilidad de tu código.

En el próximo artículo, exploraremos los [Iteradores Asíncronos](../iteradores-asincronos/), una extensión de los generadores para manejar flujos de datos asíncronos.

***

<br>
