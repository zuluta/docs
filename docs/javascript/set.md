---
hide:
  #- navigation
  - toc
---

<link rel="stylesheet" href="../../assets/stylesheets/javascript.css">

# **Set**

El objeto `Set` es una estructura de datos que permite almacenar valores únicos de cualquier tipo, ya sean primitivos u objetos. A diferencia de los arrays, un `Set` elimina automáticamente los valores duplicados, lo que lo convierte en una herramienta ideal para manejar colecciones de datos únicas de manera eficiente.

## **¿Qué es un Set en JavaScript?**

Un `Set` es una colección ordenada de valores que asegura que cada elemento sea único. Esto significa que no puede contener dos elementos con el mismo valor, aunque estos valores pueden ser de cualquier tipo, incluidos objetos y funciones.

### **¿Por qué usar Set en lugar de un Array?**

Aunque los arrays son muy versátiles, no eliminan automáticamente los valores duplicados y pueden ser menos eficientes en ciertas operaciones, como búsqueda o eliminación de elementos. Por esta razón `Set` es útil en escenarios como:

  - Eliminar duplicados en listas grandes.
  - Realizar operaciones de conjuntos (unión, intersección, diferencia).
  - Mantener datos únicos con búsquedas rápidas.

**Sintaxis Básica:**

```js linenums="1" title="javascript"
const conjunto = new Set();
```

También se puede inicializar con un array de valores:

```js linenums="1" title="javascript"
const conjunto = new Set([1, 2, 3, 4, 4]);

console.log(conjunto);
```

## **Propiedades y Métodos Principales de Set**

El objeto `Set` incluye propiedades y métodos para gestionar fácilmente sus elementos.

### **Propiedad `size`**

La propiedad `size` devuelve el número total de elementos únicos almacenados en el `Set`.

```js linenums="1" title="javascript"
const conjunto = new Set([1, 2, 3, 3]);

console.log(conjunto.size);
```

A diferencia de los arrays, no necesitas preocuparte por duplicados ni escribir código adicional para contarlos.

### **Método `add(value)`**

El método `add` permite añadir un valor al `Set`. Si el valor ya existe, no se añadirá nuevamente. Este método es ideal cuando necesitas construir una colección única de valores dinámicamente, como cuando recorres una lista de elementos.

```js linenums="1" title="javascript"
const conjunto = new Set();
conjunto.add(10);
conjunto.add(20);
conjunto.add(10); // Ignorado porque ya existe

console.log(conjunto);
```

### **Método `delete(value)`**

El método `delete` elimina un valor específico del `Set`. Devuelve `true` si el valor fue eliminado y `false` si no existía.

```js linenums="1" title="javascript"
const conjunto = new Set();
conjunto.add(10);
conjunto.add(20);
conjunto.add(10);
conjunto.delete(10);

console.log(conjunto);
```

Este método es eficiente para eliminar valores sin necesidad de recorrer manualmente toda la colección, como sucede con los arrays.

### **Método `has(value)`**

El método `has` comprueba si un valor existe en el `Set` y devuelve un booleano (`true` o `false`). Es útil para verificar la existencia de un valor antes de realizar una operación, como agregarlo o eliminarlo.

```js linenums="1" title="javascript"
const conjunto = new Set();
conjunto.add(10);
conjunto.add(20);
conjunto.add(10);

console.log(conjunto.has(20));
console.log(conjunto.has(30));
```

### **Método `clear()`**

El método `clear` elimina todos los valores del `Set` reiniciándolo completamente. Es práctico cuando necesitas vaciar una colección temporal en lugar de crear un nuevo `Set`.

```js linenums="1" title="javascript"
const conjunto = new Set();
conjunto.add(10);
conjunto.add(20);
conjunto.add(10);
conjunto.clear();

console.log(conjunto.size);
```

## **Operaciones de Conjunto con `Set`**

Además de almacenar valores únicos, `Set` facilita la implementación de operaciones de conjunto comunes como unión, intersección y diferencia. Estas operaciones son esenciales en muchas aplicaciones matemáticas y algorítmicas.

### **Unión**

La **unión** combina todos los valores únicos de dos conjuntos. Esto se logra utilizando el operador `spread (...)` para combinar los elementos de ambos `Set`. Es útil cuando necesitas combinar listas de datos sin duplicados, como registros de usuarios o productos en diferentes bases de datos.

```js linenums="1" title="javascript"
const conjuntoA = new Set([1, 2, 3]);
const conjuntoB = new Set([3, 4, 5]);

const union = new Set([...conjuntoA, ...conjuntoB]);
console.log(union);
```

### **Intersección**

La intersección devuelve los valores que son comunes entre dos conjuntos. Esto se logra utilizando el método `filter` para comprobar qué valores de un conjunto existen en el otro. En aplicaciones prácticas, puedes usar la intersección para encontrar elementos compartidos entre dos grupos, como usuarios que pertenecen a dos listas de correos diferentes.

```js linenums="1" title="javascript"
const conjuntoA = new Set([1, 2, 3]);
const conjuntoB = new Set([3, 4, 5]);

const interseccion = new Set(
    [...conjuntoA].filter((valor) => conjuntoB.has(valor))
);
console.log(interseccion);
```

### **Diferencia**

La diferencia devuelve los valores que están en un conjunto pero no en el otro. Esto es útil para identificar elementos únicos en un grupo. Es común en casos como detectar elementos que faltan en una lista o verificar datos eliminados.

```js linenums="1" title="javascript"
const conjuntoA = new Set([1, 2, 3]);
const conjuntoB = new Set([3, 4, 5]);

const diferencia = new Set(
    [...conjuntoA].filter((valor) => !conjuntoB.has(valor))
);
console.log(diferencia);
```

### **Ejemplo Básico: Filtrar Palabras Únicas**

Supongamos que necesitas identificar todas las palabras únicas en una oración. Con un `Set`, esto se logra de manera eficiente:

```js linenums="1" title="javascript"
const texto = 'JavaScript es divertido, JavaScript es poderoso';
const palabras = texto.toLowerCase().split(/\W+/);

const unicas = new Set(palabras);
console.log(unicas);
```

En casos como análisis de texto o procesamiento de datos, los `Set` permiten obtener resultados únicos con un código más simple.

## **Diferencias entre Set y Arrays**

Aunque los arrays y los `Set` tienen características similares, sus diferencias clave determinan cuándo es mejor usar cada uno.

| Característica            | Set	     | Array                     |
| :------------------------ | :--------- | :------------------------ |
| Valores Únicos            | Sí	     | No                        |
| Eliminación de Duplicados | Automática | Requiere código adicional |
| Rendimiento en Búsqueda   | Mejor	     | Menos eficiente           |

***

### **Conclusión**

El objeto `Set` en JavaScript es una herramienta poderosa para manejar datos únicos de manera eficiente. Desde eliminar duplicados hasta realizar operaciones de conjunto como unión e intersección, `Set` es una alternativa versátil a los arrays en muchos casos. Comprender sus métodos y usos te ayudará a escribir código más limpio, optimizado y profesional.

***

<br>
