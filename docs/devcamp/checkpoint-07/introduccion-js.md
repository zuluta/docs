---
hide:
  #- navigation
  #- toc
---

# 1. ¿Qué diferencia a Javascript de cualquier otro lenguaje de programación?
**JavaScript** es un lenguaje de programación básico para la ==creación de sitios web dinámicos e interactivos==. Se usa en navegadores, servidores y aplicaciones para mejorar la experiencia del usuario. Aunque se llama JavaScript, no debe confundirse con Java.

Su principal ventaja es que {==se ejecuta directamente en el navegador del usuario==}, sin necesidad de compilar el código previamente.

**El flujo de ejecución es la siguiente:**

  1. ==El navegador carga el código JavaScript== en una web
  2. ==El motor de JavaScript lo interpreta y ejecuta==
  3. ==Interactúa con el DOM== (Document Object Model), que modifica elementos HTML en tiempo real
  4. ==Puede comunicarse con servidores== mediante AJAX o Fetch API para obtener y enviar datos sin recargar la página
  5. ==Maneja eventos== como clics de botones para mejorar la interactividad
<br>
<br>

**Veamos el siguiente ejemplo:**

  1. Pulsa el botón
  2. Escucha el evento click
  3. Ejecuta la función
  4. Cambia el texto del botón

```html title="ejemplo.html"
<!-- crea un boton que pone Start -->
<button class="btn-start">Start</button>
```

```js title="ejemplo.js"
// captura el elemento DOM
const btnStart = document.querySelector('.btn-start');

// captura el evento
btnStart.addEventListener('click', changeText);

// función para cambiar el texto del boton
function changeText() {
    btnStart.innerHTML = 'Texto cambiado';
}
```

**Análisis del código:**

Revisa lo que hace el código, desde ==ejemplo.js== captura el objeto DOM del ==ejemplo.html== y para ello, hace referencia a la clase =="btn-start"==. Una vez capturado el objeto DOM, lo guarda en una variable llamada ==btnStart== para luego poner en escucha y capturar el ==evento 'click'==, para ==llamar a la función changeText==.
<br>
<br>

Cuando se aprende JavaScript, es esencial entender la ==relación entre HTML, CSS y JavaScript==, y cómo se unen para mostrar un sitio web. Aunque la mayoría de las aplicaciones de JavaScript son del lado del cliente (FRONTEND), este lenguaje también es útil en aplicaciones del lado del servidor (BACKEND), como la creación de servidores web.

**Características de JavaScript:**

  - **Multiparadigma**: Soporta programación orientada a objetos, funcional e imperativa
  - **Dinámico y flexible**: No requiere declaración explícita de tipos de datos
  - **Basado en eventos**: Responde a interacciones del usuario
  - **Compatible con todos los navegadores**: Funciona en cualquier navegador moderno
  - **Asíncrono y concurrente**: Permite manejar tareas en paralelo con promesas y async/await

!!! success "Ventajas"
    - Es fácil de aprender y usar.
    - Se ejecuta en el navegador, sin necesidad de compilación
    - Amplia compatibilidad con diferentes plataformas
    - Ecosistema extenso con miles de librerías y frameworks
    - ==Soporte para desarrollo full-stack con Node.js==

!!! failure "Desventajas"
    - Manejo de errores menos estricto comparado con otros lenguajes
    - Uso excesivo puede afectar el rendimiento de una página web
<br>

### 1.1. Sintaxis de JavaScript
JavaScript tiene una serie de {==normas básicas de sintaxis==} que debemos seguir.

**Variables:**

puedes declarar variables usando las palabras clave `var`, `const` o `let`.

  - `let` Permite declarar variables limitando su alcance al bloque, fuera de ella no tiene efecto
  - `const` Son como las `let`, solo que su valor no cambiara a lo largo del programa
  - `var` Permite declarar variables con alcance dentro y fuera del bloque, se entienden como globales.

!!! info "IMPORTANTE"
    No se recomienda el uso de `var` en Javascript, porque puede dar lugar a problemas y confusiones.

**Punto y coma para finalizar sentencias:**

En JavaScript, cada instrucción generalmente termina con un `;` punto y coma. ==Es una buena práctica usar el punto y coma siempre==. De lo contrario, puede dar errores.

**Instrucciones y ejecución secuencial:**

En JavaScript, el código está compuesto por instrucciones que ==se ejecutan de forma secuencial==. Esto significa que las instrucciones se ejecutan una tras otra, de arriba hacia abajo, en el orden en que aparecen.

**Llaves para delimitar bloques de código:**

Las llaves `{}` en JavaScript se utilizan para ==definir bloques de código==, especialmente en estructuras de control como funciones, bucles o condiciones.

**Sensibilidad a mayúsculas y minúsculas:**

==JavaScript es un lenguaje que diferencia entre mayúsculas y minúsculas== (case-sensitive). Esto significa que distingue entre nombre, Nombre y NOMBRE, considerándolos variables diferentes.

### <p style="color:#308830;">Buenas prácticas al nombrar variables:</p>

  - Aunque JavaScript no lo exige, es de ==buena práctica utilizar camelCase== para nombrar variables
  - Una variable ==no puede comenzar con un número==.
  - Un nombre de variable ==no puede contener espacios==.
  - ==No pueden incluir símbolos especiales== como (==!==, ==@==, ==#==, ==%==) a excepción del guion bajo (_) y el símbolo de dólar ($).

### <p style="color:#e11918;">Algunas palabras reservadas:</p>

  - **Control de flujo**: ==if==, ==else==, ==switch==, ==case==, ==default==
  - **Ciclos**: ==for==, ==while==, ==do==, ==break==, ==continue==
  - **Declaración de variables y funciones**: ==var==, ==let==, ==const==, ==function==, ==return==
  - **Manipulación de objetos y clases**: ==class==, ==extends==, ==constructor==, ==super==
  - **Valores especiales**: ==null==, ==undefined==, ==true==, ==false==
  - **Operaciones asincrónicas**: ==async==, ==await==
  - **Operadores de importación/exportación**: ==import==, ==export==
  - **Operadores lógicos y aritméticos**: ==new==, ==delete==, ==typeof==, ==instanceof==

!!! warning "PRECAUCIÓN"
    Estas palabras son utilizadas por el lenguaje para funciones específicas y su uso como nombres provocará errores.
<br>

### 1.2. Comentarios en JavaScript
Su propósito es proporcionar explicaciones o notas para los desarrolladores que leen el código. En JavaScript, los comentarios ==pueden ser de dos tipos==.

  - **Comentarios** ==de una sola línea==
  - **Comentarios** ==de varias líneas==
<br>

### Comentarios de una sola línea:
Los ==comentarios de una sola línea== comienzan con dos barras inclinadas (`//`). Todo el texto que sigue a estas barras en la misma línea es considerado un comentario y es ignorado por el intérprete de JavaScript.

```js title="ejemplo.js"
// Este es un comentario de una sola línea
let nombre = "Roberto"; // También se puede usar al final de una línea de código
```

### Comentarios de varias líneas:
Los ==comentarios de varias líneas== se encierran entre `/*` y `*/`. Todo el texto dentro de estos delimitadores es considerado un comentario y es ignorado por el intérprete.

```js title="ejemplo.js"
/*
Este es un comentario de varias líneas.
Puede abarcar múltiples líneas.
Es útil para explicaciones más largas o para desactivar bloques de código.
*/
let edad = 36;
```
<br>

### 1.3. Cómo usar la consola en JavaScript
En JavaScript la consola se usa contínuamente. El método mas utilizado es `console.log`. Su propósito principal es ==imprimir información en la consola==.

**Veamos el siguiente ejemplo:**

```js title="ejemplo.js"
let mensaje = '¡Hola mundo!';

// varios ejemplos de salida:
console.log(mensaje); // ¡Hola mundo!
console.log(`Este es mi primer ${mensaje}`); // Este es mi primer ¡Hola mundo!
```

Esto es útil para verificar que las variables contienen los valores esperados y que el flujo de ejecución es el correcto.
<br>

### 1.4. Cómo usar la ventana emergente en JavaScript
En JavaScript la **ventana emergente** se usa contínuamente. El método mas utilizado es `alert`. Su propósito principal es ==imprimir información en la ventana emergente==.

**Veamos el siguiente ejemplo:**

```js title="ejemplo.js"
let mensaje = '¡Hola mundo!';

// varios ejemplos de salida:
alert(mensaje) // ¡Hola mundo!
alert(`Este es mi primer ${mensaje}`); // Este es mi primer ¡Hola mundo!
```

Esto es útil para verificar que las variables contienen los valores esperados y que el flujo de ejecución es el correcto.
<br>

### 1.5. Indentación de código
A medida que escribimos líneas de código en nuestro programa, este se irá complicando y nos tomará más tiempo leer lo que hemos hecho y comprobar si hay errores o buscar como solucionarlos. Sin embargo, para mejorar la rapidez con la que leemos y entendemos el código, ==una buena práctica es usar la indentación==.

**A la hora de indentar código hay dos opciones:**

  - Usar ==espacios==
  - Usar ==tabuladores==

Utilizar una u otra estrategia de tabulación depende del programador, pero lo importante es siempre utilizar la misma. En mis ejemplos, suelo utilizar ==indentación a 4 espacios== porque me resulta más práctico leer.
<br>
<br>
