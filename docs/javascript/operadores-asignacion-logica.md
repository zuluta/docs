---
hide:
  #- navigation
  - toc
---

<link rel="stylesheet" href="../../assets/stylesheets/javascript.css">

# **Operadores de Asignación Lógica**

Los operadores de asignación lógica combinan una [operación lógica](../operadores-logicos/) (AND, OR o fusión de nulos) con una asignación. Esto permite evaluar una condición y asignar el resultado a una variable solo si se cumple el criterio del operador lógico correspondiente.

En JavaScript, los operadores de asignación lógica son:

  - `&&=`: Asignación condicional usando AND.
  - `||=`: Asignación condicional usando OR.
  - `??=`: Asignación condicional usando fusión de nulos.

><br>
> Estos operadores son particularmente útiles para establecer valores predeterminados y para simplificar el código que de otra manera requeriría estructuras condicionales más complejas.
>
><br>

La siguiente tabla muestra la equivalencia de los operadores de asignación lógica:

| Asignación Lógica | Operadores Lógicos |
| :---------------- | :----------------- |
| x \|\|= y	        | x \|\| (x = y)     |
| x &&= y	        | x && (x = y)       |
| x ??= y	        | x ?? (x = y)       |

## **Operador de Asignación Lógica OR**

El operador `||=` (OR lógico de asignación) asigna un valor a una variable solo si la variable actual tiene un valor “falsy” (es decir, `false`, `null`, `undefined`, `0`, `NaN`, o `""`). Si la variable ya tiene un valor “truthy” (que no es `null`, `undefined`, etc.), el operador no realiza la asignación.

```js linenums="1" title="javascript"
variable ||= valorPredeterminado;
```

Por ejemplo: En el siguiente ejemplo, `nombre` es una cadena vacía (`""`) que se evalúa como `false`. Por lo tanto, `nombre` toma el valor `"Invitado"`

```js linenums="1" title="javascript"
let nombre = "";
nombre ||= "Invitado";

console.log(nombre);
```

El operador `||=` es ideal para asignar valores predeterminados o inicializar variables solo cuando su valor actual es “falsy”.

Vemos otro ejemplo:

```js linenums="1" title="javascript"
let title = 'JavaScript es Increíble';
title ||= 'sin título';

console.log(title);
```

En este ejemplo la constante `title` es ‘JavaScript es Increíble’ por lo que es `truthy`. Por lo tanto el operador de asignación lógica OR (`||=`) no asigna el string ‘sin título’ a la variable `title`.

Al igual que el [operador lógico OR](../operadores-logicos/), la asignación lógica OR también tiene cortocircuito. Esto significa que el operador de asignación lógica OR solo realiza una asignación cuando x es falsy.

## **Operador de Asignación Lógica AND**

El operador `&&=` (AND lógico de asignación) asigna un valor a una variable solo si la variable actual es “truthy” (es decir, no es `false`, `null`, `undefined`, `0`, `NaN`, o `""`). Si la variable es “falsy”, el operador no realiza la asignación.

```js linenums="1" title="javascript"
variable &&= nuevoValor;
```

Por ejemplo: En el siguiente ejemplo, como `permisos` es `true`, se asigna el valor `"Administrador"`. Si `permisos` hubiera sido `false`, la asignación no se habría ejecutado.

```js linenums="1" title="javascript"
let permisos = true;
const acceso = "Administrador";

permisos &&= acceso;
console.log(permisos);
```

Este operador es útil para actualizar un valor solo cuando se cumple una condición específica, como cuando un usuario tiene permisos o un estado está activo.

## **Operador de Fusión de Nulos de Asignación**

El operador `??=` asigna un valor a una variable solo si esta es `null` o `undefined`. A diferencia de `||=`, el operador `??=` no considera valores `0`, `""`, o `false` como `null` o `undefined`, permitiendo asignar valores predeterminados solo cuando la variable está realmente vacía.

```js linenums="1" title="javascript"
variable ??= valorPredeterminado;
```

Por ejemplo: En el siguiente ejemplo `usuario` es `null`, por lo que se le asigna `"Invitado"`. Si `usuario` hubiera sido `""` o `0`, no se habría realizado la asignación.

```js linenums="1" title="javascript"
let usuario = null;
usuario ??= "Invitado";

console.log(usuario);
```

El operador `??=` es ideal para asignar valores predeterminados solo en los casos en que la variable es `null` o `undefined`, lo cual puede ser útil en la gestión de valores opcionales.

Veamos otro ejemplo:

```js linenums="1" title="javascript"
const user = {
  username: 'Satoshi'
};
user.nickname ??= 'anónimo';

console.log(user);
```

En el anterior ejemplo `user.nickname` es `undefined`, por lo tanto es nullish. El operador de asignación de fusión nula asigna el string ‘anónimo’ a la propiedad `user.nickname`.

## **Buenas Prácticas con Operadores de Asignación Lógica**

  - **Prefiere `??=` para Valores Opcionales**: Usa `??=` cuando necesitas un valor predeterminado solo si la variable es `null` o `undefined`, evitando reemplazar (`0`) o un string vacío (`""`) involuntariamente.
  - **Usa `||=` para Valores Predeterminados Flexibles**: Utiliza `||=` cuando una variable pueda tener múltiples valores “falsos” (`0`, `NaN`, `""`), pero quieras asignar un valor predeterminado si es necesario.
  - **Aprovecha `&&=` para Condiciones Específicas**: `&&=` es útil para establecer valores cuando una condición es verdadera, especialmente en casos donde se requiere que una variable ya tenga un valor “truthy”.

***

### **Conclusión**

Los operadores de asignación lógica en JavaScript (`||=`, `&&=`, `??=`) permiten realizar asignaciones de forma condicional en una sola línea. Cada operador tiene su propio uso, permitiendo optimizar el código y evitar asignaciones innecesarias.

En el próximo artículo exploraremos [Operador de Fusión de Nulos en JavaScript](../operador-fusion-nulos/)

***

<br>
