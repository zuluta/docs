---
hide:
  #- navigation
  #- toc
---

## **Como crear elementos HTML con JS**

En este ejemplo, vamos a crear un elemento párrafo ==p== dentro de un ==div== **padre**.
```html linenums="1" title="html"
<div id='padre'></div>
```

Usando appendChild:

```js linenums="1" title="javascript"
const divPadre = document.getElementById('divPadre');

const nuevoElemento = document.createElement('p');
nuevoElemento.textContent = '¡Hola mundo!';

divPadre.appendChild(nuevoElemento);
```

**Explicación:**

  - ==document.getElementById('divPadre')== Selecciona el elemento div con el ID divPadre.
  - ==document.createElement('p')== Crea un nuevo elemento p.
  - ==nuevoElemento.textContent = '¡Hola mundo!'== Establece el contenido del nuevo elemento.
  - ==divPadre.appendChild(nuevoElemento)== Agrega el nuevo elemento como hijo del divPadre.

### **Alternativa (Usando innerHTML):**

```js
divPadre.innerHTML += '<p>Hola, mundo!</p>';
```

Este método es más simple, pero no permite crear elementos dinámicamente con características específicas (como clases o atributos).

### **Para agregar atributos al nuevo elemento:**

```js linenums="1" title="javascript"
nuevoElemento.setAttribute('class', 'mi-clase');
nuevoElemento.setAttribute('id', 'mi-id');
```

>Nota: Si el div ya tiene contenido, el nuevo elemento se agregará al final de ese contenido.

***

<br>
