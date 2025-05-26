---
hide:
  #- navigation
  #- toc
---

## **DOM añadir y eliminar estilos**

Cuando trabajamos con estilos CSS en JS, una tarea común es la de cambiar los estilos de los elementos DOM. Para seleccionar elementos DOM, hay diferentes metodos:

  - ==getElementById==
  - ==getElementsByClassName==
  - ==getElementsByTagName==
  - ==querySelector==
  - ==querySelectorAll==

### **Cambia el nombre de la clase:**

```html linenums="1" title="html"
<div id="titulo" class="disabled">
  Cambia el color del título.
</div>
```

```css linenums="1" title="css"
.active {
    color: green;
    font-size: 1rem;
}

.disabled {
    color: red;
    font-size: 1rem;
}
```

```js linenums="1" title="javascript"
let titulo = document.getElementById('titulo');

titulo.className = 'active';
```

***

### **Crea una propiedad en la clase:**

En este ejemplo, agrega un margen de 20px a la clase **titulo**

```html linenums="1" title="html"
<div id="titulo">Agregame 20px de margen</div>
```

```css linenums="1" title="css"
let tarjeta = document.getElementById('titulo');
tarjeta.style.margin = "20px";
```

***

<br>
