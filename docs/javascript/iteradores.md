---
hide:
  #- navigation
  - toc
---

<link rel="stylesheet" href="../../assets/stylesheets/javascript.css">

# **Introducción a los Iteradores**

Los iteradores en JavaScript proporcionan una manera eficiente y controlada de recorrer secuencias de datos. A través del protocolo de iteración, los iteradores permiten acceder secuencialmente a los elementos de una colección sin la necesidad de usar bucles tradicionales como `for` o `while`.

En este artículo exploraremos los conceptos básicos de los iteradores, cómo se implementan y sus casos de uso más comunes.

## **¿Qué es un iterador?**

Un iterador es un objeto que permite recorrer una secuencia de datos mediante el método `next()`. Cada vez que se llama a este método, se devuelve un objeto con dos propiedades:

  - `value`: el valor actual en la secuencia.
  - `done`: un booleano que indica si la secuencia ha terminado (`true` si ha terminado, `false` en caso contrario).

Ejemplo básico de un iterador:

```js linenums="1" title="javascript"
function crearIterador(array) {
    let indice = 0;
    return {
        next: function () {
            if (indice < array.length) {
                return { value: array[indice++], done: false };
            } else {
                return { done: true };
            }
        }
    };
}

const iterador = crearIterador([1, 2, 3]);

console.log(iterador.next());
console.log(iterador.next());
console.log(iterador.next());
console.log(iterador.next());
```

En el ejemplo anterior `crearIterador` devuelve un objeto iterador para recorrer un array. Cada llamada a `next()` avanza al siguiente elemento en la secuencia.

## **Protocolos de iteración en JavaScript**

JavaScript define dos protocolos de iteración esenciales que los objetos deben seguir para ser considerados iterables y usarse en bucles como `for...of`.

### 1. **Protocolo de Iterador**

Un objeto es un iterador si implementa un método `next()`, el cual devuelve un objeto con las propiedades `value` y `done`. Este protocolo define cómo deben comportarse los iteradores.

```js linenums="1" title="javascript"
const iterador = {
    current: 1,
    last: 5,
    next() {
        if (this.current <= this.last) {
            return { value: this.current++, done: false };
        } else {
            return { done: true };
        }
    }
};

console.log(iterador.next());
console.log(iterador.next());
```

El iterador devuelve números desde `current` hasta `last`. Cuando se alcanza el último número, `done` pasa a ser `true`.

### 2. **Protocolo de Iterable**

Un objeto es iterable si implementa el método `Symbol.iterator`, que devuelve un iterador. Esto permite que el objeto sea recorrido mediante estructuras como `for...of` o el operador de propagación.

```js linenums="1" title="javascript"
const objetoIterable = {
    [Symbol.iterator]() {
        let paso = 0;
        return {
            next() {
                paso++;
                return paso <= 3 ? { value: paso, done: false } : { done: true };
            }
        };
    }
};

for (const valor of objetoIterable) {
    console.log(valor); 
}
```

El método `Symbol.iterator` define cómo se generan los valores al recorrer el objeto. Se utiliza `for...of` para iterar de forma sencilla.

## **¿Por qué usar iteradores en JavaScript?**

Los iteradores ofrecen una serie de ventajas al permitir un control completo sobre el proceso de iteración. Aquí hay algunas razones para utilizarlos:

  1. **Control secuencial**: Permiten recorrer elementos en un orden específico, ideal para secuencias personalizadas.
  2. **Iteración personalizada**: Los desarrolladores pueden definir exactamente cómo y cuándo avanzar en una colección.
  3. **Legibilidad**: Mejoran la claridad del código, especialmente en estructuras complejas.

## **Creación de Iteradores Personalizados**

Podemos crear iteradores personalizados implementando el protocolo de iterador con el método `next()`. Este enfoque es ideal para recorrer secuencias o estructuras de datos que no son inherentemente iterables, como objetos personalizados.

**Ejemplo de un Iterador Personalizado con un Rango de Números**

```js linenums="1" title="javascript"
const rango = {
    inicio: 1,
    fin: 5,
    [Symbol.iterator]() {
        let actual = this.inicio;
        let fin = this.fin;
        return {
            next() {
                return actual <= fin
                    ? { value: actual++, done: false }
                    : { done: true };
            }
        };
    }
};

for (const numero of rango) {
    console.log(numero);
}
```

En este caso `rango` es un objeto que genera números entre `inicio` y `fin`. La implementación de `Symbol.iterator` permite usar `for...of` para iterar fácilmente sobre el rango.

### **Limpieza de recursos con el método return**

El método `return()` en el iterador permite liberar recursos o ejecutar lógica cuando se detiene la iteración antes de completar la secuencia. Este método se invoca automáticamente si el bucle `for...of` finaliza prematuramente.

```js linenums="1" title="javascript"
const iterableConReturn = {
    [Symbol.iterator]() {
        let index = 0;
        return {
            next() {
                if (index < 3) {
                    return { value: index++, done: false };
                } else {
                    return { done: true };
                }
            },
            return() {
                console.log("Iteración detenida, liberando recursos.");
                return { done: true };
            }
        };
    }
};

for (const valor of iterableConReturn) {
    if (valor > 1) break;
    console.log(valor);
}
```

En el código anterior el método `return()` permite ejecutar una limpieza cuando se interrumpe la iteración.

## **Buenas Prácticas con Iteradores**

  - **Usa `Symbol.iterator` para definir secuencias personalizadas**: Implementa este método solo cuando necesitas un control avanzado sobre la iteración.
  - **Evita iteradores complejos sin necesidad**: Utiliza iteradores personalizados únicamente cuando no puedas resolver el problema con estructuras nativas como arrays o maps.
  - **Utiliza `return` para liberar recursos**: Si la iteración puede detenerse antes de completarse, implementa el método `return()` para evitar problemas de memoria.

***

### **Conclusión**

Los iteradores son una herramienta poderosa para manejar secuencias de datos en JavaScript. Al dominar los protocolos de iteración y el uso de `Symbol.iterator`, puedes crear iteradores personalizados y optimizar la manera en que interactúas con estructuras de datos complejas.

En el próximo artículo profundizaremos en el concepto de [Iterables y el uso de for…of](../bucle-for-of/) para iterar eficientemente sobre diferentes tipos de datos en JavaScript.

***

<br>
