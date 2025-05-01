---
hide:
  #- navigation
  - toc
---

<link rel="stylesheet" href="../../assets/stylesheets/javascript.css">

# **Valores Primitivos vs. Valores de Referencia**

En JavaScript existen dos tipos principales de valores: **valores primitivos** y **valores de referencia**. La forma en que se almacenan y manejan en la memoria es distinta para cada tipo, lo que afecta cómo funcionan la asignación, la comparación y la manipulación de estos valores.

En este artículo aprenderás las diferencias entre los valores primitivos y los valores de referencia, así el cómo se almacenan en la memoria, el uso de la pila (stack) y el montón (heap), ademas de buenas prácticas al trabajar con ellos.

## **Tipos de Valores en JavaScript**

JavaScript tiene dos tipos diferentes de valores:

### **1. Valores Primitivos:**

Los valores primitivos son los [tipos de datos](../tipos-de-datos/) más básicos y simples en JavaScript. Son inmutables, lo que significa que no pueden ser modificados una vez creados. En lugar de modificar el valor, JavaScript crea un nuevo valor cuando se realiza una operación sobre un valor primitivo.

  - **`number`**: Representa valores numéricos, tanto enteros como decimales.
  - **`string`**: Cadenas de texto.
  - **`boolean`**: Valores lógicos `true` o `false`.
  - **`undefined`**: Indica que una variable ha sido declarada pero no inicializada.
  - **`null`**: Representa la ausencia intencional de un valor.
  - **`symbol`**: Identificadores únicos introducidos en ES6.
  - **`bigint`**: Para representar números enteros muy grandes, a partir de ES2020.

### **2. Valores de Referencia:**

Los valores de referencia son estructuras de datos complejas que no almacenan los valores directamente, sino una referencia a la ubicación en memoria donde se encuentran. Esto significa que cuando se asigna un valor de referencia a una variable, se copia la referencia y no el valor en sí.

  - **Objetos**: Colección de pares clave-valor.
  - **Arrays**: Listas ordenadas de elementos, que son un tipo especial de objeto.
  - **Funciones**: Objetos invocables que pueden contener lógica de programación.
  - **Fechas** (`Date`), **Expresiones regulares** (`RegExp`), entre otros.

## **¿Cómo se Almacenan en Memoria? (Referencia vs. Copia)**

La forma en que se almacenan los valores en la memoria depende de si son valores primitivos o de referencia. Esta diferencia es clave para entender cómo se comportan en operaciones de asignación y comparación.

### **1. Valores Primitivos: Almacenamiento por Copia**

Los valores primitivos se almacenan directamente en la memoria de pila (stack). Cuando se asigna un valor primitivo a una variable se almacena una copia del valor en la memoria. Por lo tanto, modificar el valor de una variable no afecta a otras variables que contengan el mismo valor.

```js linenums="1" title="javascript"
let a = 10;
let b = a;  // b es una copia de a
b = 20;

console.log(a);
console.log(b);
```

En el anterior código `a` y `b` son independientes porque almacenan copias separadas del valor.

### **2. Valores de Referencia: Almacenamiento por Referencia**

Los valores de referencia se almacenan en la **memoria de montón** (**heap**), y la variable contiene una referencia (puntero) a la ubicación del objeto en la memoria. Cuando se asigna un valor de referencia a otra variable se copia la referencia, no el objeto en sí. Esto significa que cualquier cambio en el objeto afectará a todas las variables que apuntan a ese mismo objeto.

```js linenums="1" title="javascript"
const objeto1 = { nombre: "Ana" };
const objeto2 = objeto1;  // objeto2 apunta al mismo objeto en el heap

objeto2.nombre = "María";

console.log(objeto1.nombre);
```

En este caso, tanto `objeto1` como `objeto2` apuntan al mismo objeto en la memoria, por lo que los cambios realizados a través de cualquiera de las variables son visibles desde ambas.

## **Memoria de pila y montón (Stack & heap)**

La memoria en JavaScript se divide en dos áreas principales: **la pila** (**stack**) y **el montón** (**heap**), que tienen diferentes propósitos y características.

### **1. Memoria de Pila (Stack)**

La pila es una región de la memoria que se usa para almacenar valores primitivos y para gestionar el contexto de ejecución de funciones. Cada vez que se declara una variable con un valor primitivo se asigna en la pila, lo que permite un acceso rápido y eficiente.

  - **Almacenamiento por valor**: Cada valor se almacena directamente.
  - **Acceso rápido**: El acceso a los datos en la pila es muy rápido debido a la forma en que la memoria se organiza.
  - **Vida corta**: Los datos almacenados en la pila son de vida corta y se eliminan cuando se sale del ámbito de ejecución.

### **2. Memoria de Montón (Heap)**

El montón es una región de la memoria utilizada para almacenar valores de referencia, como objetos y arrays. Es un área menos estructurada que la pila, lo que permite almacenar grandes cantidades de datos dinámicos.

  - **Almacenamiento por referencia**: Los valores no se almacenan directamente; en su lugar, se almacena una referencia a su ubicación en el montón.
  - **Mayor complejidad de acceso**: El acceso a los datos en el montón es más lento que en la pila debido a su estructura menos organizada.
  - **Vida larga**: Los datos en el montón pueden persistir durante más tiempo y solo se eliminan cuando ya no son referenciados (recolección de basura).

## **Propiedades dinámicas**

Un valor de referencia en JavaScript permite la manipulación dinámica de sus propiedades, lo que implica la capacidad de agregar, cambiar o eliminar propiedades en cualquier momento. Por ejemplo, en un objeto podemos añadir nuevas propiedades, modificar las existentes o eliminarlas según sea necesario:

```js linenums="1" title="javascript"
let person = {
  name: 'John',
  age: 25,
};

// Agregar una nueva propiedad
person.city = 'Madrid';

// Modificar una propiedad existente
person.age = 31;

// Eliminar una propiedad
delete person.age;
```

Por otro lado, los valores primitivos no admiten la adición de propiedades ya que no son objetos y por lo tanto no tienen métodos o propiedades propias que puedan ser modificadas dinámicamente. Intentar agregar una propiedad a un valor primitivo no tendrá efecto alguno:

```js linenums="1" title="javascript"
let name = 'Juan';
// Intentar agregar una propiedad a un valor primitivo
name.city = 'Madrid';

console.log(name.city);
```

Aunque no se producirá ningún error, la propiedad no se agregará al valor primitivo. Esto se debe a que JavaScript convierte temporalmente el valor primitivo en un objeto durante la operación, pero luego lo descarta, dejando el valor primitivo original sin cambios.

### **Copiar valores de variables primitivas**

Cuando copias un valor primitivo de una variable a otra en JavaScript, el motor crea una copia independiente de ese valor y lo asigna a la nueva variable. Esto significa que los cambios en una variable no afectarán a la otra.

```js linenums="1" title="javascript"
let num1 = 10;
let num2 = num1; // Se copia el valor de num1 en num2

num1 = 20; // Cambiamos el valor de num1

console.log(num1);
console.log(num2);
```

En el anterior ejemplo inicializamos `num1` con el valor `10`. Luego, copiamos este valor en `num2`. Después, modificamos el valor de `num1` a `20`, pero `num2` sigue manteniendo su valor original de `10`, ya que es una copia independiente del valor de `num1`.

### **Copiar referencias de variables de objetos**

Cuando asignas un valor de referencia de una variable a otra en JavaScript, el motor crea una referencia que apunta al mismo objeto en la memoria del montón para ambas variables. Esto implica que cualquier cambio realizado en una de las variables se reflejará en la otra.

```js linenums="1" title="javascript"
let obj1 = { name: 'John' };
let obj2 = obj1; // Se crea una referencia a obj1 en obj2

obj1.name = 'Alice'; // Cambiamos el nombre en obj1

console.log(obj1.name);
console.log(obj2.name);
```

En este ejemplo, `obj1` y `obj2` hacen referencia al mismo objeto en la memoria del montón. Por lo tanto, cuando cambiamos el nombre en `obj1`, este cambio también se refleja en `obj2`, ya que ambas variables apuntan al mismo objeto.

***

### **Conclusión**

Comprender la diferencia entre **valores primitivos y de referencia en JavaScript** es importante para trabajar eficientemente con el lenguaje. Saber cómo se almacenan en la memoria y las implicaciones de la pila y el montón te ayudará a escribir código más seguro y evitar errores comunes relacionados con la mutabilidad y la manipulación de datos.

***

<br>
