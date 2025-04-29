---
hide:
  #- navigation
  - toc
---

<link rel="stylesheet" href="../../assets/stylesheets/javascript.css">

# **Primeros pasos**

**JavaScript es un lenguaje de programación interpretado**, orientado a objetos y de alto nivel. Originalmente fue creado para añadir interactividad en las páginas web, permitiendo que los sitios respondan a las acciones del usuario, como hacer clic en botones, mover el ratón o enviar formularios. Con el paso de los años, su uso ha crecido y hoy en día se utiliza tanto en el frontend (*lo que ves en el navegador*) como en el backend (*el servidor*).

Una de las características más atractivas de JavaScript es que es compatible con todos los navegadores modernos. Esto significa que puedes escribir JavaScript en cualquier página HTML sin necesidad de configuraciones adicionales, funcionará en todos.

## **Cómo insertar JavaScript en tu HTML**

Para empezar a usar JavaScript en tu página web es fundamental saber cómo se integra con HTML, el lenguaje de marcado que estructura las páginas web.

Existen dos formas básicas de incluir JavaScript en un documento HTML:

  1. **Incrustación Directa**: El código se embebe directamente en la página HTML
  2. **Archivo Externo**: Referenciar a un archivo de código JavaScript externo.

## **Incrustar código JavaScript en una página HTML**

Una forma sencilla y rápida de comenzar a usar JavaScript es escribir el código directamente en el mismo archivo HTML, dentro de etiquetas `<script>`. Esta técnica es útil para proyectos pequeños o para cuando necesitas agregar scripts específicos que no serán reutilizados en otras páginas. Aunque esta opción es válida, no es la más recomendable para proyectos más complejos o escalables.

```html linenums="1" title="html"
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Mi Página Web</title>
  <script>
    console.log("¡Hola desde JavaScript!");
  </script>
</head>
<body>
  <h1>Contenido de la página</h1>
</body>
</html>
```

Esta forma es útil para pequeños fragmentos de código o para ejecutar scripts específicos en una página en especifico.

## **Incluir un archivo JavaScript externo**

A medida que los proyectos crecen y se vuelven más complejos, es buena práctica separar el código JavaScript en archivos independientes con extensión `.js` Estos archivos se enlazan al documento HTML a través de la etiqueta `<script>` con el atributo que define la fuente de origen `src`.

Esta forma permite un código más organizado, facilita el mantenimiento y la reutilización del código en diferentes partes del proyecto.

```html linenums="1" title="html"
<!DOCTYPE html>
<html lang="es">
<head>
  <title>Mi Página Web</title>
  <script src="./script.js"></script>
</head>
<body>
  <h1>Contenido de la página</h1>
</body>
</html>
```

En este caso, el archivo `script.js` está en el mismo directorio que el archivo `.html`.

Usar archivos JavaScript externos es especialmente útil cuando trabajas en equipo, ya que permite que múltiples personas trabajen en diferentes archivos de manera simultánea sin interferir en el código HTML.

### **Ventajas de Usar Archivos Externos**

El uso de archivos externos en lugar de incrustar el código JavaScript directamente en el HTML tiene varias ventajas:

  - **Reutilización**: Puedes usar el mismo archivo JavaScript en diferentes páginas de tu sitio web sin necesidad de copiar y pegar el código en cada una de ellas.
  - **Mantenimiento**: Separar la estructura HTML del comportamiento JavaScript facilita hacer cambios en el código sin afectar el contenido visual de la página.
  - **Mejoras de rendimiento**: Los navegadores modernos pueden almacenar en caché los archivos JavaScript externos, lo que reduce el tiempo de carga en visitas posteriores a la página.

### **Ruta del Archivo Externo:**

La ruta del archivo externo te permite enlazar archivos desde otros directorios utilizando `..` para navegar hacia arriba en la jerarquía de directorios.

```html linenums="1" title="html"
<script src="../public/js/script.js"></script>
```

En el ejemplo anterior “`..`” indica que estamos retrocediendo un nivel en la jerarquía de directorios. Luego, accedemos al directorio “==public==”, después al subdirectorio “==js==” y finalmente al archivo “`script.js`”.

### **Enlace a Archivos Externos de Terceros:**

También es posible enlazar archivos JavaScript alojados en servidores externos, como bibliotecas o CDNs. Un ejemplo común es la inclusión de jQuery desde su CDN.

```html linenums="1" title="html"
<script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
```

***

## **Incluir Múltiples Archivos JavaScript en un Archivo**

Incluir múltiples archivos JavaScript en una página web es posible mediante la inclusión de varias etiquetas `<script>` en el código HTML. El motor JavaScript interpreta estos archivos en el orden en que aparecen.

Por ejemplo:
```html linenums="1" title="html"
<script src="js/functions.js"></script>
<script src="js/app.js"></script>
```

En este ejemplo, el motor JavaScript interpreta primero el archivo `functions.js` y luego `app.js`, en secuencia. **Es importante tener en cuenta este orden, ya que las funciones y variables definidas en `functions.js` estarán disponibles para su uso en `app.js`**.

Cuando una página incluye muchos archivos JavaScript externos, puede ocurrir que la página se muestre en blanco durante la fase de renderizado. Para evitar este problema, se recomienda incluir los archivos JavaScript justo antes del cierre de la etiqueta `</body>`, como se muestra a continuación:

```html linenums="1" title="html"
<!DOCTYPE html>
<html>
<head>
    <!-- Otros elementos del encabezado -->
</head>
<body>
    <!-- Contenido de la página -->

    <!-- Scripts al final del cuerpo -->
    <script src="js/functions.js"></script>
    <script src="js/app.js"></script>
</body>
</html>
```

***

## **Los Atributos Async y Defer:**

En la práctica, es importante que el JavaScript no bloquee el renderizado del contenido de la página, especialmente cuando se trabaja con muchos archivos o bibliotecas externas. Aquí es donde entran en juego los atributos `async` y `defer` de la etiqueta `<script>`.

### **Atributo Async (Asíncrono):**

El atributo `async` permite que el script se descargue en paralelo con la página. Esto puede mejorar la velocidad de carga porque el navegador no tiene que esperar a que el script se descargue y ejecute antes de continuar renderizando el resto del contenido.

Sin embargo `async` no garantiza que los scripts se ejecuten en el orden en que se declaran, lo que puede causar problemas si un script depende de otro.

```html linenums="1" title="html"
<script async src="js/functions.js"></script>
<script async src="js/app.js"></script>
```

En el ejemplo anterior el archivo `app.js` podría ejecutarse antes que el archivo `functions.js`. Por lo tanto, debes asegurarte de que no exista dependencia entre ellos.

### **Atributo Defer (Diferir):**

El atributo `defer` por otro lado, asegura que los scripts se ejecuten en el orden en que aparecen en el documento HTML. Además, garantiza que el script no se ejecute hasta que el navegador haya terminado de procesar completamente el HTML, lo que puede ser útil para asegurarse de que el DOM esté listo para interactuar con el JavaScript.

```html linenums="1" title="html"
<script defer src="js/app.js"></script>
```

Aunque coloquemos el elemento `<script>` en el `<head>`, el script esperará hasta que el navegador reciba el elemento `</html>` de cierre para comenzar a ejecutarse.
***

## **Buenas Prácticas en la Inclusión de JavaScript**

A medida que los proyectos web crecen, es útil seguir ciertas prácticas recomendadas para asegurarse de que el código sea mantenible, eficiente y fácil de entender para otros desarrolladores.


  1. **Ubicación de las etiquetas `<script>`**: Aunque puedes colocar las etiquetas `<script>` en la cabecera del documento HTML (`<head>`), una mejor práctica es colocarlas justo antes de la etiqueta de cierre del cuerpo (`</body>`). Esto asegura que el contenido de la página se cargue antes de ejecutar cualquier script, mejorando la experiencia del usuario y la percepción de la velocidad de carga de la página.
  2. **Modularidad**: A medida que tu código JavaScript crece, es recomendable dividirlo en módulos. Desde la llegada de ES6, JavaScript soporta módulos nativos, lo que facilita la organización del código en partes reutilizables y bien definidas.
  3. **Uso de herramientas para mejorar el código**: Para mantener una alta calidad en el código, herramientas como ESLint y Prettier juegan un papel importante. Estas herramientas analizan el código en busca de errores de sintaxis, inconsistencias o malas prácticas. Además, pueden formatear automáticamente el código para seguir un estilo consistente.

***

## **Compatibilidad con Todos los Navegadores**

Uno de los aspectos más importantes al trabajar con JavaScript es asegurarse de que tu código funcione correctamente en diferentes navegadores. Aunque la mayoría de los navegadores modernos soportan las últimas características de JavaScript, algunos, especialmente los más antiguos, pueden no ser compatibles con ciertas funciones avanzadas.

### **Uso de Polyfills**

Los **polyfills** son fragmentos de código que permiten que las funcionalidades modernas de JavaScript se ejecuten en navegadores antiguos. Por ejemplo, si deseas usar la función `Array.prototype.includes()`, que no está disponible en todos los navegadores, puedes incluir un polyfill para asegurarte de que funcione en navegadores que no soportan esta función.

***

### **Conclusión:**

JavaScript es un lenguaje extremadamente poderoso y versátil que ha evolucionado significativamente desde sus inicios. Saber cómo integrarlo correctamente en tus proyectos HTML es solo el primer paso para desbloquear su potencial. Al seguir buenas prácticas, usar módulos y aprovechar las herramientas disponibles para mejorar la calidad del código, podrás crear aplicaciones web más rápidas, eficientes y fáciles de mantener.

***

<br>
