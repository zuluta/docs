---
hide:
  #- navigation
  - toc
---

<link rel="stylesheet" href="../../assets/stylesheets/javascript.css">

# **Introducción a los Objetos**

En JavaScript, los objetos son una de las estructuras de datos más importantes y versátiles. Permiten almacenar múltiples valores bajo una misma entidad, lo que facilita la organización y manipulación de datos complejos. Los objetos se utilizan para representar entidades del mundo real y sus características como propiedades y comportamientos.

En este artículo exploraremos los conceptos fundamentales de los objetos en JavaScript, incluyendo cómo crear, acceder y modificar sus propiedades.

## **¿Qué es un Objeto en JavaScript?**

Un objeto en JavaScript es una colección de pares clave-valor, donde cada clave (también llamada propiedad) es un identificador único asociado a un valor. Los valores pueden ser de cualquier [tipo válido en JavaScript](../tipos-de-datos/), incluyendo números, cadenas de texto, booleanos, funciones e incluso otros objetos.

Los objetos permiten agrupar información relacionada en una sola estructura, lo que resulta útil para representar entidades complejas del mundo real. Por ejemplo, puedes usar un objeto para modelar las características de una persona, como su nombre, edad y género o las propiedades de un auto, como su marca, modelo y año.

**Ejemplo de un Objeto Básico:**

```js linenums="1" title="javascript"
const persona = {
  nombre: "Juan",
  edad: 30,
  esEstudiante: true
};
```

En este ejemplo `persona` es un objeto con tres propiedades: `nombre`, `edad` y `esEstudiante`. Cada propiedad tiene un nombre único y un valor asociado.

## **Creación de Objetos en JavaScript**

Hay varias formas de crear objetos en JavaScript, siendo las más comunes la notación literal y el uso del constructor `Object()`. Elegir un método u otro depende del caso de uso y de las preferencias del desarrollador.

### **1. Notación Literal**

La forma más común y sencilla de crear un objeto es utilizando la **notación literal**, que consiste en definir el objeto directamente entre llaves `{}` con sus pares clave-valor. Este método es ideal cuando se conoce de antemano la estructura del objeto.

```js linenums="1" title="javascript"
const auto = {
  marca: "Toyota",
  modelo: "Corolla",
  anio: 2022
};
```

En el snippet anterior se crea el objeto `auto` con tres propiedades: `marca`, `modelo` y `anio`. La notación literal es concisa y fácil de leer, por lo que es la opción preferida en la mayoría de los casos.

### **2. Uso del Constructor `Object()`**

El constructor `Object()` es otra forma de crear objetos, aunque no es tan utilizada como la notación literal. Es útil cuando se necesita crear un objeto vacío y agregar propiedades de forma dinámica o cuando se trabaja con programación más orientada a objetos.

```js linenums="1" title="javascript"
const libro = new Object();
libro.titulo = "El principito";
libro.autor = "Antoine de Saint-Exupéry";
libro.publicacion = 1943;

console.log(libro);
```

Ambos métodos permiten crear objetos, pero la notación literal es generalmente más práctica y legible.

## **Acceso a las Propiedades de un Objeto**

Para trabajar con los datos almacenados en un objeto es necesario saber cómo acceder a sus propiedades. En JavaScript se puede hacer esto usando la notación de punto (`objeto.propiedad`) o la notación de corchetes (`objeto["propiedad"]`). Ambos métodos son equivalentes en funcionalidad, pero se usan en diferentes contextos.

**Ejemplos de Acceso a Propiedades:**

```js linenums="1" title="javascript"
const persona = {
  nombre: "María",
  edad: 25
};

// Usando notación de punto
console.log(persona.nombre);

// Usando notación de corchetes
console.log(persona["edad"]);
```

La notación de punto es más concisa y se utiliza con mayor frecuencia, mientras que la notación de corchetes es útil cuando el nombre de la propiedad es dinámico o contiene caracteres especiales.

## **Modificación de las Propiedades de un Objeto**

Una de las ventajas de los objetos en JavaScript es que sus propiedades se pueden modificar en tiempo de ejecución. Esto significa que puedes actualizar el valor de una propiedad existente, añadir nuevas propiedades o incluso eliminar propiedades que ya no son necesarias. Esta flexibilidad permite trabajar con datos dinámicos, adaptando la estructura del objeto según las necesidades del programa.

**Ejemplo de Modificación de Propiedades:**

```js linenums="1" title="javascript"
const mascota = {
  nombre: "Firulais",
  tipo: "Perro"
};

// Modificando una propiedad existente
mascota.nombre = "Max";

// Añadiendo una nueva propiedad
mascota.edad = 4;

console.log(mascota);
```

En este ejemplo, se cambia el nombre de la mascota y se añade una nueva propiedad `edad`. Este tipo de operaciones son comunes en aplicaciones donde los datos pueden cambiar con el tiempo.

## **Eliminación de Propiedades en un Objeto**

A veces es necesario eliminar propiedades de un objeto para reducir su tamaño o limpiar datos que ya no son relevantes. En JavaScript, se utiliza la palabra clave `delete` para eliminar propiedades de un objeto. Esta operación es permanente y elimina la propiedad completamente, junto con su valor asociado.

**Ejemplo de Eliminación de Propiedades:**

```js linenums="1" title="javascript"
const usuario = {
  nombre: "Carlos",
  correo: "carlos@example.com"
};

// Eliminando la propiedad correo
delete usuario.correo;

console.log(usuario); 
```

El uso del operador `delete` permite gestionar mejor la memoria y mantener los objetos limpios y organizados.

Aunque `delete` elimina la propiedad del objeto, si se accede a ella posteriormente, se obtendrá `undefined`.

## **Comprobación de Propiedades en un Objeto**

En ocasiones es útil verificar si un objeto tiene una propiedad específica antes de manipularla. Para esto JavaScript ofrece dos formas principales: el operador `in` y el método `hasOwnProperty()`. Estos métodos ayudan a evitar errores al acceder a propiedades inexistentes y permiten verificar la estructura del objeto antes de realizar operaciones.

**Ejemplos de Comprobación:**

```js linenums="1" title="javascript"
const producto = {
  nombre: "Laptop",
  precio: 1200
};

// Usando el operador 'in'
console.log("nombre" in producto);

// Usando el método hasOwnProperty()
console.log(producto.hasOwnProperty("precio"));
```

Estos métodos son esenciales para trabajar con objetos en aplicaciones más complejas, donde la estructura de los datos puede ser variable.

***

### **Conclusión**

Los objetos en JavaScript son una parte fundamental del lenguaje, permitiendo modelar y gestionar datos de manera eficiente. Comprender cómo crear, modificar y eliminar propiedades es esencial para trabajar con aplicaciones que manejan datos complejos. Esta introducción proporciona las bases para trabajar con objetos, mientras que los temas avanzados se abordan en una sección específica.

***

<br>
