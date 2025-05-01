---
hide:
  #- navigation
  - toc
---

<link rel="stylesheet" href="../../assets/stylesheets/javascript.css">

# **Operadores de Comparación**

Los operadores de comparación en JavaScript permiten comparar valores para evaluar condiciones. Estos son el núcleo de la lógica de un programa, permitiendo evaluar condiciones y dirigir el flujo de un script con base en resultados específicos, ya que tomar decisiones inteligentes en código depende de la capacidad de comparar valores de forma precisa y eficiente.

En este artículo exploraremos a fondo cómo funcionan, qué casos de uso resuelven y cómo emplearlos para escribir código más robusto y confiable.

## **¿Qué es un Operador de Comparación?**

Los operadores de comparación comparan dos valores y devuelven un [valor booleano](../tipos-de-datos/) (`true` o `false`). En JavaScript, estos operadores se utilizan comúnmente en declaraciones condicionales para determinar el flujo del programa.

***

## **Operadores de Igualdad**

JavaScript ofrece dos tipos de operadores de igualdad: igualdad débil (`==`) y igualdad estricta (`===`). Ambos permiten comparar valores, pero se comportan de manera distinta respecto a la conversión de tipos.

### **1. Igualdad Débil (`==`)**

El operador `==` compara dos valores después de convertir sus tipos (si es necesario). Esta conversión implícita puede producir resultados inesperados si no se usa con precaución.

```js linenums="1" title="javascript"
console.log(5 == "5");  // (convierte "5" a número)
console.log(true == 1); // (convierte true a 1)
console.log(null == undefined); // (ambos se tratan como iguales)
```

Aunque la igualdad débil puede ser conveniente, es recomendable evitarla para evitar errores en la lógica del programa.

### **2. Igualdad Estricta (`===`)**

El operador `===` compara valores sin realizar ninguna conversión de tipos. Esto significa que ambos valores deben tener el mismo tipo y valor para que la comparación sea `true`.

```js linenums="1" title="javascript"
console.log(5 === "5");  // (no convierte "5" a número)
console.log(true === 1); // (distintos tipos)
console.log(null === undefined); // (diferentes valores)
```

Usa `===` siempre que sea posible, ya que proporciona una comparación más precisa y evita errores de conversión de tipo.

## **Operadores de Desigualdad**

Los operadores de desigualdad también pueden realizar comparaciones con o sin conversión de tipos. Existen dos variantes: desigualdad débil (`!=`) y desigualdad estricta (`!==`).

### **1. Desigualdad Débil (`!=`)**

El operador `!=` compara valores y realiza una conversión de tipos si es necesario, devolviendo `true` si los valores son diferentes.

```js linenums="1" title="javascript"
console.log(5 != "5");  // (convierte "5" a número)
console.log(false != 0); // (convierte false a 0)
console.log(null != undefined); // (ambos se consideran iguales)
```

### **2. Desigualdad Estricta (`!==`)**

El operador `!==` compara dos valores sin realizar conversión de tipos. Devuelve `true` solo si los valores y tipos son distintos.

```js linenums="1" title="javascript"
console.log(5 !== "5");  // (diferentes tipos)
console.log(false !== 0); // (distintos tipos)
console.log(null !== undefined); // (diferentes valores)
```

**Consejo**: Al igual que con `===`, usa `!==` para garantizar que la comparación respete el tipo de datos y evitar conversiones implícitas.

## **Comparación de valores Mayor que / Menor que**

Los operadores de mayor y menor se utilizan para comparar valores numéricos. También pueden utilizarse con strings, donde comparan en base al orden lexicográfico. Estos operadores siguen las siguientes reglas:

  - (Mayor que) `>` : Devuelve `true` si el valor de la izquierda es mayor que el de la derecha.
  - (Menor que) `<` : Devuelve `true` si el valor de la izquierda es menor que el de la derecha.
  - (Mayor o igual que) `>=` : Devuelve `true` si el valor de la izquierda es mayor o igual al de la derecha.
  - (Menor o igual que) `<=` : Devuelve `true` si el valor de la izquierda es menor o igual al de la derecha.

**Ejemplo de Comparación de Números:**

```js linenums="1" title="javascript"
const a = 10;
const b = 5;

console.log(a > b);
console.log(a < b);
console.log(a >= 10);
console.log(b <= 5);
```

### **Comparación de Strings**

Cuando se comparan strings, JavaScript evalúa su orden alfabético basado en la posición de los caracteres en Unicode.

```js linenums="1" title="javascript"
console.log("banana" > "apple");
console.log("2" > "12"); // (compara carácter a carácter)
```

Para evitar confusión con strings numéricos (`"2"` y `"12"`), conviértelos a números antes de comparar.

## **Comparar un Booleano Con Otro Valor**

Si un valor es booleano, JavaScript lo convierte en un número y compara el valor convertido con el otro valor; `true` se convierte a `1` y `false` se convierte a `0`.

```js linenums="1" title="javascript"
console.log(true > 0);
console.log(false < 1);
console.log(true > false);
console.log(false > true);
console.log(true >= true);
console.log(true <= true);
console.log(false <= false);
console.log(false >= false);
```

Además de las reglas anteriores, los operadores igual (`==`) y no igual (`!=`) también tienen las mismas reglas.

## **Comparación Especial con `Object.is()`**

El método `Object.is()` es similar al operador `===` pero trata algunos casos de forma distinta, proporcionando una comparación más precisa en ciertas situaciones:

  1. `NaN` se considera igual a `NaN`.
  2. `+0` y `-0` se consideran diferentes.

```js linenums="1" title="javascript"
console.log(Object.is(NaN, NaN));
console.log(Object.is(+0, -0));
console.log(Object.is(5, 5));
```

**Cuándo Usar `Object.is()`**: Este método es útil cuando necesitas una comparación estricta y quieres evitar el problema de NaN o los signos opuestos de `0`.

## **Comparar null y undefined**

Comparar `null` y `undefined` en JavaScript es interesante. Ambos representan la ausencia de un valor pero tienen comportamientos ligeramente diferentes al compararlos entre sí o con otros valores.

Cuando se comparan directamente `null` y `undefined` son iguales en valor, pero no en tipo (`null` es de tipo “object” y `undefined` es de tipo “undefined”). Sin embargo, cuando se comparan con otros valores, tanto `null` como `undefined` se convierten en `0`, lo que puede generar resultados inesperados en las comparaciones numéricas. Veamos esto en ejemplos:

```js linenums="1" title="javascript"
console.log(null == undefined);
console.log(null === undefined);

console.log(null == 0);
console.log(undefined == 0);

console.log(null < 0);
console.log(undefined < 0);
```

## **Buenas Prácticas con Operadores de Comparación**

  1. **Prefiere `===` y `!==` sobre `==` y `!=`**: La igualdad estricta y desigualdad estricta evitan problemas de conversión implícita y garantizan comparaciones precisas.
  2. **Usa `Object.is()` para Comparaciones Especiales**: En casos donde necesites comparar `NaN` o distinguir entre `+0` y `-0`, `Object.is()` proporciona mayor precisión.
  3. **Convierte Strings Numéricos Antes de Comparar**: Para evitar errores al comparar strings que representan números, conviértelos a número con `+` o `Number()`.

***

### **Conclusión**

Los operadores de comparación en JavaScript son herramientas esenciales para evaluar condiciones. Comprender las diferencias entre igualdad débil y estricta, así como los casos especiales de `Object.is()`, permite escribir código más preciso y evitar errores comunes en la lógica. Al dominar estos operadores, puedes realizar comparaciones efectivas para cualquier tipo de dato.

En el próximo artículo exploraremos los [Operadores Lógicos en JavaScript](../operadores-logicos/) y cómo utilizarlos para combinar y evaluar condiciones múltiples.

***

<br>
