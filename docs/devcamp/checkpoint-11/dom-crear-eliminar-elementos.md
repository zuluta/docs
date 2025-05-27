---
hide:
  #- navigation
  #- toc
---

## **Como crear elementos DOM con JS**


En este ejemplo, vamos a crear un elemento párrafo ==p== dentro de un ==div== **padre**.

```html linenums="1" title="html"
<div id='padre'></div>
```

### **Crear un elemento con `appendChild`:**

```js linenums="1" title="javascript"
const divPadre = document.getElementById('divPadre');

const nuevoElemento = document.createElement('p');
nuevoElemento.textContent = '¡Hola mundo!';

divPadre.appendChild(nuevoElemento);
```

**Detalles:**

  - ==document.getElementById('divPadre')== Selecciona el elemento div con el ID divPadre.
  - ==document.createElement('p')== Crea un nuevo elemento p.
  - ==nuevoElemento.textContent = '¡Hola mundo!'== Establece el contenido del nuevo elemento.
  - ==divPadre.appendChild(nuevoElemento)== Agrega el nuevo elemento como hijo del divPadre.

### **Crear un elemento con `innerHTML`:**

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

## **Como eliminar elementos DOM con JS**

Para eliminar un elemento del DOM en JavaScript, se puede utilizar el método `remove()`. Este método elimina el elemento del DOM directamente, sin necesidad de referenciar su nodo padre. También se puede usar `removeChild()` en el nodo padre, pero `remove()` es más simple en la mayoría de los casos.

### **Eliminar un elemento con `remove()`:**

En este ejemplo, vamos a eliminar un elemento ==div== **mi-elemento**.

```html linenums="1" title="html"
<div id='mi-elemento'></div>
```

```js linenums="1" title="javascript"
const elemento = document.getElementById('mi-elemento');
elemento.remove();
```

### **Eliminar un elemento con `removeChild()`:**

En este ejemplo, vamos a eliminar un elemento ==div== **hijo** dentro de un ==div== **mi-elemento**.

```html linenums="1" title="html"
<div id='mi-elemento'>
  <div id="hijo"></div>
</div>
```

```js linenums="1" title="javascript"
const elemento = document.getElementById('mi-elemento');
const hijo = document.getElementById('hijo');
elemento.removeChild(hijo);
```

**Detalles:**

  - ==remove()== El método remove() es la opción más sencilla y directa para eliminar un elemento del DOM. Simplemente se llama en el elemento que se desea eliminar.
  - ==removeChild()== Este método se usa para eliminar un nodo hijo de su nodo padre. Es necesario primero obtener el nodo padre y luego invocar el método removeChild() en él, pasando como argumento el nodo hijo a eliminar.
  - ==innerHTML = ' '== Si se necesita eliminar todos los hijos de un nodo, se puede utilizar innerHTML = ' ' para establecer el contenido del nodo a una cadena vacía. Esto efectúa una eliminación masiva de los hijos del nodo, lo que puede ser útil en ciertos escenarios.

***

### **Eliminar multiples elementos con un bucle `while` y `remove()`:**

En este ejemplo, vamos a eliminar todos los elementos de clase **post** que encuentre dentro del documento HTML.

```html linenums="1" title="html"
<div class="post-container">
  <div class="post">Post 1</div>
  <div class="post">Post 2</div>
  <div class="post">Post 3</div>
  <div class="post">Post 4</div>
</div>
<div class="post">Post 5</div>
```

```js linenums="1" title="javascript"
const postContainer = document.querySelector('.post-container');
const post = document.getElementsByClassName('post');

const newElement = document.createElement('p');
newElement.className = 'flash-message';
newElement.textContent = 'Posts coming soon!';

while (post.length > 0) {
  post[0].remove();
}

postContainer.appendChild(newElement);
```

***

### **Eliminar multiples elementos con `forEach` y `remove()`** (método recomendado)

En este ejemplo, vamos a eliminar todos los elementos de clase **post** que encuentre dentro del documento HTML.

```html linenums="1" title="html"
<div class="post-container">
  <div class="post">Post 1</div>
  <div class="post">Post 2</div>
  <div class="post">Post 3</div>
  <div class="post">Post 4</div>
</div>
<div class="post">Post 5</div>
```

```js linenums="1" title="javascript"
const postContainer = document.querySelector('.post-container');
const post = document.querySelectorAll('.post');

const nuevoElemento = document.createElement('p');
nuevoElemento.className = 'mensaje-flash';
nuevoElemento.textContent = '¡Próximamente habrá publicaciones!';

post.forEach(elemento => elemento.remove());

postContainer.appendChild(nuevoElemento);
```

**Nota:** ==forEach== recorre cada elemento del array, comenzando desde el primer elemento y terminando con el último. Es una forma concisa de recorrer un array sin la necesidad de usar bucles tradicionales como for o while.

***

<br>
