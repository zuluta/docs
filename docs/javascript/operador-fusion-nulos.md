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

