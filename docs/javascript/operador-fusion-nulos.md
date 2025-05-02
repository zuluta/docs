---
hide:
  #- navigation
  - toc
---

<link rel="stylesheet" href="../../assets/stylesheets/javascript.css">

# **Operador de Fusión de Nulos**

Introducido en ES2020, el operador de fusión de nulos (`??`) es una solución elegante para asignar valores predeterminados solo cuando una variable es `null` o `undefined`. A diferencia del [operador lógico](../operadores-logicos/) `||`, que trata valores “falsy” como `0`, `false` o `""` de manera similar a `null`, el operador `??` preserva estos valores válidos, ofreciendo un control más preciso sobre los datos opcionales.

En este artículo desglosaremos cómo funciona el operador de fusión de nulos (**coalescente nulo**), por qué es superior en ciertos casos y cómo puedes utilizarlo para escribir código más limpio y confiable al gestionar valores predeterminados.

## **¿Qué es el Operador de Fusión de Nulos?**

El operador de fusión de nulos (`??`) es una entidad que evalúa el valor de la izquierda y si es `null` o `undefined`, devuelve el valor de la derecha. Si el valor de la izquierda es cualquier otro valor, incluyendo `0`, `""`, o `false`, devuelve dicho valor sin pasar al valor predeterminado de la derecha.

```js linenums="1" title="javascript"
const resultado = exprIzquierda ?? exprDerecha;
```

  - `exprIzquierda` es el valor que se evalúa primero.
  - `exprDerecha` es el valor que se asigna solo si `exprIzquierda` es `null` o `ndefined`.

Técnicamente el operador coalescente nulo es equivalente al siguiente bloque:

```js linenums="1" title="javascript"
const result = value1;

if(result === null || result === undefined) {
 result = value2;
}
```

Veamos otro ejemplo básico donde la variable `edad` se establecerá en `28` ya que el primer valor es indefinido, por lo que el operador de fusión de nulos devuelve el segundo valor (`28`).

```js linenums="1" title="javascript"
const edad = undefined ?? 28;

console.log(edad);
```

El operador de fusión de nulos es útil para proporcionar valores predeterminados en caso de que el valor inicial sea nulo o indefinido, lo que simplifica y hace más legible el código.

### **Ejemplos de Uso: Asignación de Valores Predeterminados**

El operador de fusión de nulos es útil para asignar un valor predeterminado solo cuando una variable es `null` o `undefined`.

```js linenums="1" title="javascript"
const nombreUsuario = null;
const nombre = nombreUsuario ?? "Invitado";

console.log(nombre);
```

En el anterior ejemplo `nombreUsuario` es `null`, por lo que `nombre` toma el valor `"Invitado"`. Si `nombreUsuario` hubiera tenido un valor distinto de `null` o `undefined`, `nombre` se habría asignado con ese valor.

### **Evitar Sobrescribir Valores “Falsy”**

A diferencia del operador `||` el operador `??` permite retener valores “falsy” como `0`, `false`, y `""`, en lugar de reemplazarlos con un valor predeterminado.

```js linenums="1" title="javascript"
const puntuacion = 0;
const puntuacionFinal = puntuacion ?? 100;

console.log(puntuacionFinal);
```

En el anterior ejemplo `puntuacion` es `0`, un valor “falsy” pero válido, por lo que `puntuacionFinal` toma el valor `0` en lugar de `100`.

## **Diferencia entre el operador lógico OR y Fusión de Nulos**

El operador lógico OR `||` también se usa para asignar valores predeterminados, pero considera cualquier valor “falsy” como `false`, `0`, `NaN`, `""`, `null`, o `undefined`. Esto significa que el operador `||` sustituirá valores que pueden ser válidos en algunos casos.

**Ejemplo Comparativo:**

```js linenums="1" title="javascript"
const texto = "";
const mensaje1 = texto || "Texto predeterminado";
const mensaje2 = texto ?? "Texto predeterminado";

console.log(mensaje1);
console.log(mensaje2);
```

En el ejemplo anterior `||` reemplaza el string vacío `""` por `"Texto predeterminado"`, mientras que `??` respeta `""` como un valor válido.

Usa `??` cuando desees conservar valores “falsy” como `0`, `false`, o `""`, y reserva `||` para asignaciones donde cualquier valor “falsy” deba ser reemplazado.

## **El Operador de Fusión de Nulos y su Cortocircuito**

Al igual que los [operadores lógicos](../operadores-logicos/), el operador de fusión de nulos también presenta un comportamiento de cortocircuito.

**Funcionamiento del Cortocircuito**: El operador de fusión de nulos no evalúa el segundo valor si el primer operando no es `undefined` ni `null`. Esto significa que si el primer valor ya es un valor definido, no se evalúa ni se ejecuta la segunda expresión.

```js linenums="1" title="javascript"
const result = 1 ?? console.log('Hola JavaScript');
```

En el anterior ejemplo vemos como el primer valor es `1` (su tipo no equivale a `null` ni `undefined`), el operador de fusión de nulos no necesita evaluar la segunda expresión `console.log('Hi')`. Por lo tanto, no se mostrará el mensaje “Hola JavaScript” en la consola.

```js linenums="1" title="javascript"
const result = undefined ?? console.log('Hola Programador');
```

En este caso, como el primer valor es `undefined` el operador de fusión de nulos evaluará la segunda expresión `console.log('Hola Programador')` y mostrará su valor en la consola.

**Ventajas del Cortocircuito:**

  - Mejora el rendimiento al evitar evaluaciones innecesarias.
  - Aumenta la eficiencia del código al evitar operaciones redundantes.
  - Garantiza un comportamiento predecible al priorizar la eficacia sobre la evaluación exhaustiva.

***

## **Encadenamiento con Operadores Lógicos y Fusión de Nulos**

Cuando se utilizan operadores lógicos como OR y AND junto con el operador de fusión de nulos, es importante considerar la precedencia de los operadores para evitar errores sintácticos.

```js linenums="1" title="javascript"
const result = null || undefined ?? 'OK';

console.log(result)
```

En este ejemplo se produce un error de sintaxis porque la combinación directa del operador OR con el operador de fusión de nulos no sigue la precedencia de los operadores.

Para evitar este error se recomienda utilizar paréntesis para especificar explícitamente la precedencia de los operadores:

```js linenums="1" title="javascript"
const result = (null || undefined) ?? 'OK';

console.log(result);
```

Al envolver la expresión a la izquierda del operador de fusión de nulos entre paréntesis, se asegura que la evaluación se realice de manera correcta y sin errores sintácticos.

><br>
> Al encadenar operadores lógicos con el operador de fusión de nulos, es esencial prestar atención a la precedencia de los operadores y utilizar paréntesis para garantizar una evaluación correcta y evitar errores sintácticos en JavaScript.
>
><br>

## **Buenas Prácticas al Usar El Operador de Fusión de Nulos**

  - **Prefiere `??` para Valores Opcionales**: Utiliza este operador para asignar valores predeterminados solo cuando la variable puede ser `null` o `undefined`, sin afectar valores como `0`, `""`, o `false`.
  - **Usa `||` para Asegurar Valores “Truthy”**: Si necesitas una asignación más flexible que reemplace cualquier valor “falsy”, `||` puede ser más adecuado.
  - **Evita Mezclar `??` con Otros Operadores Lógicos sin Paréntesis**: JavaScript no permite combinar `??` con `&&` o `||` sin usar paréntesis, ya que puede causar ambigüedad en la evaluación de las expresiones.

***

### **Conclusión**

El operador de fusión de nulos (`??`) en JavaScript permite asignar valores de manera segura solo cuando una variable es `null` o `undefined`, sin reemplazar otros valores “falsy” como `0`, `false`, o `""`. Al entender la diferencia entre `??` y `||`, puedes controlar mejor las asignaciones condicionales en tu código, evitando sobrescribir valores válidos. Este operador es especialmente útil en la configuración de valores predeterminados y en la verificación de propiedades opcionales en objetos.

***

<br>
