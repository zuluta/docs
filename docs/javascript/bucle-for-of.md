---
hide:
  #- navigation
  - toc
---

<link rel="stylesheet" href="../../assets/stylesheets/javascript.css">

# **Iterables y el Bucle for…of**

Los iterables en JavaScript son estructuras que permiten recorrer sus elementos de manera secuencial mediante el protocolo de iteración. Este protocolo define cómo se accede a los elementos de un objeto, haciéndolo compatible con el bucle `for...of`, lo que simplifica la iteración sobre datos como arrays, strings y estructuras personalizadas.

En este artículo exploraremos cómo funcionan los iterables, cómo implementar el protocolo de iteración y cómo el bucle `for...of` aprovecha estas capacidades.

## **¿Qué es un objeto iterable?**

Un objeto iterable es cualquier estructura de datos que implemente el método `Symbol.iterator`. Este método devuelve un iterador que permite acceder secuencialmente a los elementos del objeto.

Los tipos de datos nativos como **arrays**, **strings**, **maps** y **sets** ya son iterables por defecto, pero también puedes convertir tus propios objetos en iterables implementando `Symbol.iterator`.

**Ejemplo básico de un iterable:**

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

En este ejemplo: Cada llamada al iterador devuelve el siguiente valor de la secuencia. El método `Symbol.iterator` devuelve un iterador.

## **El bucle for…of en JavaScript**

El bucle `for...of` es una herramienta que simplifica la iteración sobre objetos iterables. A diferencia de `for...in`, que recorre las propiedades de un objeto, `for...of` accede directamente a los valores de las estructuras iterables.

**sintaxis basica:**

```js linenums="1" title="javascript"
for (const elemento of iterable) {
    // Acceso al elemento actual en cada iteración
}
```

En el siguiente ejemplo el bucle `for...of` accede a cada elemento del array `numeros` y lo imprime, sin requerir el uso de índices.

```js linenums="1" title="javascript"
const numeros = [1, 2, 3];

for (const numero of numeros) {
    console.log(numero);
}
```

Este bucle es especialmente útil porque elimina la necesidad de manejar índices manualmente y ofrece una sintaxis más limpia para trabajar con iterables.

### **Comparación entre for..of y for..in**

Aunque ambos son bucles, `for...of` y `for...in` tienen propósitos muy diferentes:

  - `for...of`: Itera sobre los valores de un objeto iterable (como arrays, strings o mapas).
  - `for...in`: Itera sobre las propiedades de un objeto, tanto las propias como las heredadas.

```js linenums="1" title="javascript"
const objeto = { a: 1, b: 2, c: 3 };

for (const propiedad in objeto) {
    console.log(propiedad);  // Output: "a", "b", "c"
}

const array = [10, 20, 30];
for (const valor of array) {
    console.log(valor);  // Output: 10, 20, 30
}
```

## **Iteración de Strings con for…of**

En JavaScript, las cadenas de texto son iterables, lo que significa que cada carácter se trata como un elemento separado en la iteración.

**Ejemplo de `for...of` con un String**

```js linenums="1" title="javascript"
const saludo = "Hola";

for (const letra of saludo) {
    console.log(letra);
}
```

Esto es particularmente útil para manipular texto, como verificar caracteres o construir nuevas cadenas basadas en ciertas condiciones.

## **Creación de iterables personalizados**

Para hacer que un objeto sea iterable, simplemente se le agrega el método `Symbol.iterator`. Esto es útil cuando se trabaja con estructuras de datos personalizadas, permitiendo definir la lógica de iteración para acceder a sus elementos.

```js linenums="1" title="javascript"
const rango = {
    inicio: 1,
    fin: 5,
    [Symbol.iterator]() {
        let actual = this.inicio;
        const fin = this.fin;
        return {
            next() {
                if (actual <= fin) {
                return { value: actual++, done: false };
                } else {
                return { done: true };
                }
            }
        };
    }
};

for (const numero of rango) {
    console.log(numero);
}
```

En el anterior código el objeto `rango` se convierte en iterable al implementar `Symbol.iterator`, la lógica de iteración se define dentro del método `next()`.

## **Buenas prácticas al usar `for...of`**

  1. **Usa `for...of` para estructuras iterables**: Es ideal para recorrer arrays, strings y estructuras personalizadas.
  2. **Evita `for...in` en arrays o strings**: Como `for...in` recorre propiedades en lugar de valores, puede no funcionar correctamente con estructuras iterables.
  3. **Define iterables personalizados según sea necesario**: Implementa `Symbol.iterator` solo si necesitas un control avanzado sobre la iteración.

***

### **Conclusión**

Los iterables y el bucle `for...of` son herramientas esenciales para manejar colecciones de datos de manera eficiente y legible en JavaScript. Al entender el protocolo iterable y cómo implementar iteradores personalizados, puedes optimizar la interacción con estructuras de datos, tanto nativas como personalizadas.

En el próximo artículo, exploraremos los [Generadores en JavaScript](../generadores/), que ofrecen una forma avanzada de crear y gestionar iteraciones con pausas controladas.

***

<br>
