---
hide:
  #- navigation
  #- toc
---

## **DOM añadir y eliminar estilos**

### Cambia el nombre de la clase con `getElementById`:

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

### Cambia el nombre de la clase con `querySelector`:

```html linenums="1" title="html"
<div class="titulo disabled">
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
let titulo = document.querySelector('.titulo');

titulo.className = 'active';
```

***

<br>
