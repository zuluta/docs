---
hide:
  #- navigation
  - toc
---

<link rel="stylesheet" href="../../assets/stylesheets/javascript.css">

# **Operador de Resto**

En JavaScript, el operador de resto, utilizado mediante el símbolo (`%`) se usa comúnmente para calcular el residuo de una división. Aunque en muchos lenguajes de programación este operador se llama “módulo”, en JavaScript actúa técnicamente como un operador de resto, lo cual implica un comportamiento ligeramente diferente.

## **¿Qué es el Operador de Resto en JavaScript?**

El operador `%` calcula el resto de dividir el primer operando por el segundo. La sintaxis básica es:

```js linenums="1" title="javascript"
resultado = a % b;
```

En el anterior código `a` es el dividendo y `b` es el divisor. El resultado es el residuo de dividir `a` por `b`, conservando el mismo signo que el dividendo.

><br>
> El resto (o remainder) en una operación de división, donde si el dividendo es positivo, el resto será positivo, y si el dividendo es negativo, el resto también será negativo.
>
><br>

### **Diferencia entre Resto y Módulo**

Aunque el operador `%` suele denominarse “módulo” en otros lenguajes (como Python), en JavaScript opera como un resto. La diferencia clave es que, en el operador de módulo verdadero, el resultado siempre es positivo, mientras que en el operador de resto el resultado sigue el signo del dividendo. Por ejemplo:

  - En **JavaScript** (resto): `-10 % 3` devuelve `-1`.
  - En **Python** (módulo): `-10 % 3` devuelve `2`.

**Implementación de un Módulo Verdadero en JavaScript:**

Si necesitas un resultado de módulo positivo (como en otros lenguajes) puedes crear una función personalizada:

```js linenums="1" title="javascript"
function modulo(a, b) {
  return ((a % b) + b) % b;
}

console.log(modulo(-10, 3));
```

Esta función asegura que el resultado sea siempre positivo, imitando el comportamiento de un operador de módulo verdadero.

## **Operador de Resto con Números Negativos**

El operador de resto devuelve el residuo con el mismo signo que el dividendo (primer operando). Este comportamiento puede ser inesperado para quienes están acostumbrados a trabajar con el módulo en otros lenguajes.

```js linenums="1" title="javascript"
const a = -10;
const b = 3;
console.log("Primer resultado: " + a % b);

const c = 10;
const d = -3;
console.log("Segundo resultado: " + c % d);
```

**En los ejemplos anteriores:**

  - `-10 % 3` devuelve `-1`, porque el signo del residuo sigue el signo del dividendo (`-10`).
  - `10 % -3` devuelve `1`, con el mismo signo positivo que `10`.

Esta diferencia en el signo puede afectar el resultado de cálculos cíclicos o patrones simétricos en el desarrollo.

## **Uso del Operador de Resto para Determinar Paridad**

El operador de resto es útil para determinar si un número es par o impar. Un número es par si el resto de dividirlo entre `2` es `0`; si el resto es `1`, el número es impar.

**Ejemplo de Verificación de Paridad:**

```js linenums="1" title="javascript"
const numero = 7;

if (numero % 2 === 0) {
  console.log(`El número ${numero} es par`);
} else {
  console.log(`El número ${numero} es impar`);
}
```

En el anterior ejemplo: `7 % 2` devuelve `1`, indicando que `7` es impar. Esta lógica es fundamental para validaciones y ciclos.

## **Conversiones y Uso de Resto con Tipos No Numéricos**

JavaScript permite usar el operador de resto con strings y otros [tipos de datos](../tipos-de-datos/), realizando conversiones automáticas. El operador convierte ambos operandos a números antes de ejecutar la operación.

### **Ejemplo de Conversión Implícita:**

```js linenums="1" title="javascript"
console.log("10" % 3);  // (convierte "10" a número)
console.log("Hola" % 2);  // (no se puede convertir a número)
```

En el primer caso, `"10"` se convierte a 10 para realizar el cálculo. En el segundo, `"Hola"` no puede convertirse, por lo que el resultado es `NaN`.

## **Aplicaciones Comunes del Operador de Resto**

  1. **Contadores Cíclicos**: Cuando se necesita reiniciar un contador al alcanzar un valor máximo este operador es ideal. Esto es útil en ciclos de colores, rotación de elementos en arrays, entre otros.

```js linenums="1" title="javascript"
const limite = 5;

for (let i = 0; i < 10; i++) {
  console.log(i % limite);
}
```

En este ciclo, `i % limite` reinicia el contador a `0` cuando `i` alcanza el limite.

  2. Validación de Múltiplos: El operador `%` permite validar si un número es múltiplo de otro. Esto es útil en algoritmos donde se aplican reglas a múltiplos específicos (por ejemplo, números divisibles por `3` o `5`).

```js linenums="1" title="javascript"
const numero = 15;

if (numero % 5 === 0) {
    console.log(`${numero} es múltiplo de 5`);
}
```

Si `numero % 5` devuelve `0`, significa que `numero` es divisible por `5`.

  3. **Alternancia en Estructuras Repetitivas**: El operador de resto / módulo permite alternar entre diferentes opciones dentro de un ciclo, como cambiar de color o patrón.

```js linenums="1" title="javascript"
const colores = ["rojo", "verde", "azul"];

for (let i = 0; i < 6; i++) {
  console.log(colores[i % colores.length]);
}
```

## **Consideraciones con el Operador de Resto**

  1. **Conoce el Signo del Resultado**: El signo sigue al dividendo, lo cual es importante en ciclos simétricos.
  2. **Comprende las Conversiones Implícitas**: `%` convierte strings numéricos automáticamente; si falla, el resultado es `NaN`.
  3. **Usa `%` para Alternancias y Ciclos**: En estructuras repetitivas este operador permite crear patrones cíclicos sin condicionales adicionales.
  4. **Aplicaciones Matemáticas y Condicionales**: Utiliza este operador en cálculos matemáticos avanzados, como comprobación de múltiplos.

***

### **Conclusión**

El operador de resto (`%`) en JavaScript es una herramienta versátil para cálculos de residuo, validación de múltiplos y patrones cíclicos. Conocer las diferencias entre resto y módulo, junto con aplicaciones prácticas, asegura un uso preciso en desarrollo. En el próximo artículo, veremos el [Operador de Exponenciación (`**`) en JavaScript](../operador-exponenciacion/).

***

<br>
