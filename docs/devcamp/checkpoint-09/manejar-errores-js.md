---
hide:
  #- navigation
  #- toc
---

## **Errores en JavaScript**

En JavaScript, un error es una situación en la que el comportamiento normal del programa se desvía debido a un problema. Los errores pueden ocurrir por diversas razones, como errores en la sintaxis del código, manipulación incorrecta de datos, intentos de acceder a elementos que no existen o problemas con recursos externos.

Los errores en JavaScript se dividen en diferentes categorías según su origen y naturaleza, estos tipos son:

  1. Errores de sintaxis.
  2. Errores de referencia.
  3. Errores de tipo.

También debemos mencionar que en el contexto de la programación, un error grave puede causar la interrupción completa e irreversible del funcionamiento de un programa. Este tipo de error generalmente está asociado con situaciones críticas que el programa no puede manejar adecuadamente y que resultan en la terminación abrupta de la ejecución.

Con respecto a los errores mencionados, los `Errores de referencia` son típicamente fatales en JavaScript y los `Errores de tipo` pueden variar en su gravedad, dependiendo de cómo se manejen.

### 1. **Errores de sintaxis**

Los errores de sintaxis, también conocidos como Syntax Erroren inglés, suceden cuando violamos las reglas de escritura de JavaScript. El motor de JavaScript puede detectarlos durante el análisis léxico y sintáctico del código. Un ejemplo común sería olvidar cerrar un paréntesis o utilizar incorrectamente una palabra reservada. Estos errores son detectados antes de ejecutar el programa y son cruciales para corregir problemas fundamentales en el código.

Ejemplo error de sintaxis:

```js linenums="1" title="javascript"
function hello(name {
    console.log("Hello, " + name);
}

hello("Diego");
```

Al ejecutar el código anterior, nos dará como resultado lo siguiente:

```
Uncaught SyntaxError: Unexpected token '{'
```

Este mensaje indica que se encontró un token (`{`) inesperado y no válido en el lugar donde se esperaba un paréntesis de cierre. Al corregir el error de sintaxis y ejecutar el código nuevamente, mostrará el saludo en la consola.

### 2. **Errores de referencia**

Los errores de referencia, también conocidos como Reference Error en inglés, suceden cuando intentamos hacer referencia a algo en nuestro código que no está definido o no es accesible en ese momento y lugar específico. Un ejemplo típico sería tratar de acceder a una variable que aún no ha sido declarada. Estos errores indican que estamos intentando utilizar algo que JavaScript no reconoce en ese contexto, y son fundamentales para corregir problemas de acceso a variables, objetos o funciones no definidos.

Ejemplo error de referencia:

```js linenums="1" title="javascript"
function getName() {
    console.log(name);
}

getName();
```

Al ejecutar el código anterior, nos dará como resultado lo siguiente:

```
Uncaught ReferenceError: name is not defined
```

Este mensaje de error indica que la variable `name` no está definida en el ámbito actual. Para solucionar este error, debemos asegurarnos de que la variable `name` esté declarada y tenga un valor asignado antes de intentar acceder a ella.

### 3. **Errores de tipo**

Los errores de tipo, también llamados Type Error en inglés, suceden cuando intentamos realizar una operación con valores que no son compatibles en cuanto a su tipo. Por ejemplo, si tratamos de realizar una operación con un tipo de dato que no es adecuado para esa acción. Estos errores señalan conflictos relacionados con los tipos de datos y son esenciales para garantizar la coherencia en nuestras operaciones, evitando que utilicemos valores de manera incorrecta o incompatible.

Ejemplo error de tipo:

```js linenums="1" title="javascript"
let text = "Hola Mundo";

let result = text.map(function (word) {
    return word.toUpperCase();
});

console.log(result);
```

Al ejecutar el código anterior, nos dará como resultado lo siguiente:

```
Uncaught TypeError: texto.map is not a function
```

Este mensaje de error indica que el método `map` no es una función válida en la variable 'text' porque las cadenas de texto no tienen ese método.

## **Lanzamiento de un objeto Error**

En JavaScript, si quieres señalar y detener la ejecución del programa cuando ocurre un problema, puedes hacerlo lanzando un objeto Error mediante la palabra clave throw. Este acto detendrá la ejecución del programa y mostrará el mensaje de error asociado. Es una forma de indicar de manera explícita que algo ha salido mal y proporciona información sobre la naturaleza del error para facilitar su corrección.

```js linenums="1" title="javascript"
throw new Error("My Error");
```

## **Captura de errores**

En JavaScript, para controlar y manejar errores, puedes emplear un bloque `try-catch`. Este bloque te permite gestionar la ejecución del programa y tomar acciones específicas cuando ocurre un error. Al rodear una porción de código con un bloque `try`, el programa intentará ejecutar ese código. Si surge un error durante la ejecución, el control se transfiere automáticamente al bloque `catch`, donde puedes definir cómo deseas manejar ese error. Esto resulta útil para gestionar situaciones inesperadas y mantener un mejor control sobre el comportamiento de tu programa.

```js linenums="1" title="javascript"
try {
    throw new Error("Ups");
} catch (error) {
    console.log(error.message); // Ups
}
```

## **Clases derivadas del objeto Error**

JavaScript no solo ofrece el objeto Error, sino que también proporciona clases derivadas como SyntaxError, TypeError, ReferenceError, entre otras. Estas clases representan errores específicos y ofrecen información adicional sobre el tipo de error que ha ocurrido. Por ejemplo, SyntaxError se relaciona con errores de sintaxis, TypeError con errores de tipo, y ReferenceError con problemas de referencia. Utilizar estas clases específicas puede ser muy útil para identificar y abordar de manera más precisa distintos tipos de errores en tu código.

```js linenums="1" title="javascript"
try {
    // Code with Error
} catch (error) {
    if (error instanceof TypeError) {
        console.log("TypeError");
    } else if (error instanceof ReferenceError) {
        console.log("ReferenceError");
    } else {
        console.log("Error");
    }
}
```

***

## **Consideración importante sobre los Errores**

Cuando lanzas un error en JavaScript, el código que sigue después del lanzamiento no se ejecutará si el error no es capturado y manejado. Si ocurre un error y no se captura, el flujo del programa se detiene y salta al primer bloque catch que pueda manejar ese tipo de error. En ausencia de un bloque catch apropiado, el programa se detiene por completo y no se ejecuta más código. Es vital capturar y manejar errores para asegurar una ejecución controlada y evitar que los problemas detengan por completo la ejecución del programa.

***

<br>
