---
hide:
  #- navigation
  #- toc
---

En JavaScript existen tres formas principales de [declarar variables](../variables/): `var`, `let` y `const`. Cada una tiene características específicas que las hacen adecuadas para diferentes situaciones. Comprender las diferencias entre ellas es importante para escribir código predecible y evitar errores comunes.

En este artículo exploraremos las particularidades de cada tipo de declaración, sus ámbitos, el comportamiento en la elevación ([hoisting](../hoisting/)), la zona muerta temporal y otros detalles clave.

## **El Ámbitos de las Variables**

El concepto de [ámbito de variable](../scope/) hace referencia a la región del código donde esta es válida y accesible. En JavaScript la palabra clave `var` tiene un ámbito global o de función, lo que significa que las variables declaradas con esta keyword pueden ser accedidas o modificadas desde fuera de un bloque específico.

Si declaramos una variable con `var` fuera de una función, esta se convierte en una variable global y puede ser accedida desde cualquier parte del código:

```js linenums="1" title="javascript"
var age = 30;

function printAge() {
  console.log(age);
}

printAge();
```

Cuando una variable se declara dentro de una función utilizando var, su alcance se limita al contexto de esa función, lo que significa que no puede ser accedida desde fuera de la función. Por ejemplo:

```js linenums="1" title="javascript"
function greet() {
  var message = "¡Hola!";
  console.log(message);
}

greet();
console.log(message);
```

Ahora, ya que tenemos el concepto del ámbito veamos que ofrece cada declaración que utilizamos para definir variables.

## **La Forma Tradicional de Declarar Variables: `var`**

`var` fue la única manera de declarar variables en JavaScript hasta la introducción de ES6. Aunque sigue siendo válida, esta presenta varias peculiaridades que pueden llevar a errores difíciles de rastrear. Veamos las principales:

  - **Ámbito global o de función**: Las variables declaradas con `var` tienen un ámbito que se limita a la función en la que se declaran o son globales si se declaran fuera de cualquier función.
  - **Permite la redeclaración**: Es posible declarar la misma variable varias veces en el mismo ámbito, lo que puede generar confusión.
  - **Hoisting**: Las variables declaradas con `var` se elevan al principio del contexto de ejecución, con un valor inicial de `undefined`.

**Ejemplo de ámbito y hoisting con `var`:**

```js linenums="1" title="javascript"
console.log(mensaje);

var mensaje = "Hola, mundo";

function saludo() {
  var mensajeInterno = "Hola desde la función";
  console.log(mensajeInterno);
}
saludo();
```

En el ejemplo anterior la variable `mensaje` se eleva y tiene un valor `undefined` antes de ser asignada, lo que muestra la naturaleza del hoisting en `var`.

### **Problema de la Creación de Propiedades Globales**

Las variables globales definidas con `var` se agregan al objeto global como propiedades adicionales. Esto puede aumentar las posibilidades de conflictos con otras bibliotecas o scripts que también utilizan el objeto global para sus propias variables.

><br>
> En el navegador web, el objeto global es window, mientras que en Node.js es global.
>
><br>

## **La Alternativa Moderna: `let`**

`let` es una mejora significativa introducida en ES6 para declarar variables de manera más segura. Su ámbito está limitado al bloque en el que se declara, lo que evita problemas comunes asociados con el uso de `var`.

**Características de `let`:**

  - **Ámbito de bloque**: Las variables declaradas con `let` solo son accesibles dentro del bloque en el que se declaran.
  - **No permite la redeclaración en el mismo ámbito**: Esto ayuda a evitar errores accidentales.
  - **Hoisting con inicialización diferida**: Aunque `let` se eleva, no se puede acceder a la variable antes de su declaración debido a la “zona muerta temporal”.

### **La Zona Muerta Temporal**

La zona muerta temporal es el período entre el inicio del bloque y la declaración de la variable `let`, durante el cual no se puede acceder a la variable. Intentar hacerlo generará un `ReferenceError`.

```js linenums="1" title="javascript"
{
    console.log(nombre);
    let nombre = "Carlos";
}
```

En el ejemplo anterior `nombre` está en la zona muerta temporal hasta que se alcanza la declaración.

## **Declaración para Constantes: `const`**

`const` se utiliza para declarar constantes, es decir, “variables porque almacena un dato” cuyo valor no puede cambiar una vez asignado. Sin embargo, si el valor es un objeto o un array sus propiedades o elementos pueden ser modificados.

**Características de `const`:**

  - **Debe ser inicializada al momento de la declaración**.
  - **No permite la reasignación**: Una vez asignado, el valor de una variable `const` no puede cambiar.
  - **Ámbito de bloque**: Al igual que `let`, las variables `const` solo están disponibles dentro del bloque en el que se declaran.

**Ejemplo de modificación de un objeto constante:**

```js linenums="1" title="javascript"
const usuario = { nombre: "Ana", edad: 30 };
usuario.edad = 31;  // Esto es válido, ya que se modifica una propiedad, no la referencia

console.log(usuario.edad);
```

## **Buenas Prácticas para Usar `var`, `let` y `const`**

  1. **Usar `const` de forma predeterminada**: Siempre que el valor de una variable no cambie usa `const` para asegurar la inmutabilidad.
  2. **Optar por `let` si necesitas cambiar el valor**: Si el valor de la variable debe cambiar, usa `let`.
  3. **Evitar `var`**: Los problemas de alcance y hoisting hacen que `var` no sea la mejor opción en la mayoría de los casos.

***

### **Conclusión**

Comprender las diferencias entre `var`, `let` y `const` es útil para escribir código limpio y seguro en JavaScript. Utilizar la opción adecuada en cada situación ayuda a evitar errores comunes y mejora la calidad del código.

En el próximo artículo nos adentraremos en los [tipos de datos en JavaScript](../tipos-de-datos/), explorando cada uno en detalle.

***

<br>
