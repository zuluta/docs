---
hide:
  #- navigation
  #- toc
---

## **¿Que es event listener?**

Un **event listener** (o manejador de eventos) en JavaScript es un procedimiento que espera a que ocurra un evento específico para reaccionar a él. En esencia, es una función que se "aplica" a un elemento del documento HTML y que se ejecuta cuando se produce el evento deseado, como un click, un cambio en un campo de texto o el envío de un formulario

***

## **Método `addEventListener`**

El método ==.addEventListener()== nos permite empezar a escuchar un evento concreto, y en el caso de que ocurra, ejecutar la función asociada.

Lista de eventos más utilizados:

  - ==click== Cuando el usuario hace clic con el botón principal del ratón.
  - ==input== Cuando el valor de un elemento <\input>, <\select>, o <\textarea> ha sido cambiado.
  - ==keyup== Cuando el usuario suelta una tecla.
  - ==focus== Cuando un elemento <\input>, <\textarea>, o elemento con tabindex obtiene el foco del usuario.
  - ==change== Cuando se modifica el valor de un elemento <\input>, <\textarea>, o <\select>.
  - ==drop== Cuando un elemento arrastrable se suelta sobre un área de destino que lo permite.
  - ==submit== Cuando se envía un formulario.

En este ejemplo, vamos a seleccionar el **segundo párrafo** por **clase** mediante `getElementsByClassName` y como evento, utilizaremos `addEventListener` ==click==.

```js linenums="1" title="html"
<p class="articulos">libro 1</p>
<p class="articulos">libro 2</p>
<p class="articulos">libro 3</p>
<button class="btn-seleccionar-articulo">Aceptar</button>
```

### **Evento + función nombrada:**

```js linenums="1" title="javascript"
// elementos DOM
const articulo = document.getElementsByClassName('articulos')[1];
const btnSeleccionarArticulo = document.querySelector('.btn-seleccionar-articulo');

// evento
btnSeleccionarArticulo.addEventListener('click', seleccionarArticulo); // invoca a la funcion

// funcion
function seleccionarArticulo() {
    const articuloSeleccionado = articulo.textContent; // captura el valor del articulo
    console.log(articuloSeleccionado); // Salida: "libro 2"
}
```

### **Evento + función anónima:**

```js linenums="1" title="javascript"
// elementos DOM
const articulo = document.getElementsByClassName('articulos')[1];
const btnSeleccionarArticulo = document.querySelector('.btn-seleccionar-articulo');

// evento + funcion flecha
btnSeleccionarArticulo.addEventListener('click', function() { // ejecuta la funcion anonima
    const articuloSeleccionado = articulo.textContent; // captura el valor del articulo
    console.log(articuloSeleccionado); // Salida: "libro 2"
});
```

### **Evento + función flecha:**

```js linenums="1" title="javascript"
// elementos DOM
const articulo = document.getElementsByClassName('articulos')[1];
const btnSeleccionarArticulo = document.querySelector('.btn-seleccionar-articulo');

// evento + funcion flecha
btnSeleccionarArticulo.addEventListener('click', () => { // ejecuta la funcion flecha
    const articuloSeleccionado = articulo.textContent; // captura el valor del articulo
    console.log(articuloSeleccionado); // Salida: "libro 2"
});
```

***

## **Agregar teclas de acceso rápido a la aplicación**

Función para detectar con una condicional si se pulsan 2 teclas específicas (ctrl + c).

```js linenums="1" title="javascript"
const atajoTeclado = (e) => {
    let windowEvent = window.event ? event : e;

    if (windowEvent.keyCode === 67 && windowEvent.ctrlKey) {
        console.log('Has pulsado la tecla ctrl + c');
    }
};

document.onkeydown = atajoTeclado;
```

***

### Fuentes:

>Sitio web: [Tabla de KeyCode](https://www.cambiaresearch.com/articles/15/javascript-char-codes-key-codes){:target="_blank"}

***

<br>
