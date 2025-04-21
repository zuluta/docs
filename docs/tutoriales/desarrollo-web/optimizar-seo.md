
Antes de subir cualquier proyecto a producción, ==es importante comprobar que el SEO (Search Engine Optimization) este correctamente construido==. Mencionare una herramienta gratuita que nos ayudara a testear nuestro SEO.

### Herramientas online:
  - [Open Graph](https://www.opengraph.xyz) es una herramienta que ==nos permitira ver la vista previa de la url compartida==
  - [Squoosh](https://squoosh.app) es una herramienta de Google para ==editar y optimizar imágenes==
<br>
<br>

### La importancia del orden:
Para optimizar el SEO, ==es necesario seguir un orden específico dentro del head==. [Harry Roberts](https://csswizardry.com/) fue el creador de este orden.
```html linenums="1"
<head>
  <meta charset | http-equiv \ viewport/>
  <title></title>
  <script src="" async></script>
  CSS that icludes @import
  Synchronous JS
  Synchronous CSS
  preload
  <script src="" defer></script>
  prefetch / prerender
  Everything else ('SEO' meta tags, icons, Open Graph, etc.)
</head>
```

### Construcción básica del head con el SEO optimizado:

  - Aquí la ==configuración general del sitio web==
    ```html linenums="1"
    <meta charset="UTF-8"/>
    <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
    mas...
    ```

  - Aquí la ==información general del sitio web==
    ```html linenums="1"
    <title>Documentación técnica</title>
    <link rel="icon" type="image/png" href="src/img/favicon.png"/>
    <meta name="description"  content="Documentación de proyectos, tutoriales de programación, guías de instalación, todo en un único lugar."/>
    mas...
    ```

  - Aquí la ==fuente de css y js==
    ```html linenums="1"
    <link rel="stylesheet" href="src/css/custom.css"/>
    <script src="src/js/custom.js"></script>
    mas...
    ```

  -  Aquí el [protocolo general de Open Graph](https://ogp.me/) que ==genera vista previa del enlace cuando es compartido==.
    ```html linenums="1"
    <meta property="og:url" content="https://zuluta.github.io"/> <!-- url a compartir -->
    <meta property="og:type" content="website"/> <!-- tipo de url a compartir -->
    <meta property="og:title" content="Documentación técnica"/> <!-- título de url a compartir -->
    <meta property="og:description" content="Documentación de proyectos, tutoriales de programación, guías de instalación, todo en un único lugar."/> <!-- descripción de url a compartir -->
    <meta property="og:image" content="https://zuluta.github.io/og.jpg"/> <!-- imagen de url a compartir -->
    <meta property="og:locale" content="es_ES"/>
    mas...
    ```

```html title="Ejemplo básico con el SEO optimizado" linenums="1"
<!DOCTYPE html>
<html lang="es">

  <!-- información que lee el navegador -->
  <head>

    <!-- configuración general del sitio web -->
    <meta charset="UTF-8"/>
    <meta name="viewport" content="width=device-width, initial-scale=1.0"/>

    <!-- información general del sitio web -->
    <title>Documentación técnica</title>
    <link rel="icon" type="image/png" href="src/img/favicon.png"/>
    <meta name="description"  content="Documentación de proyectos, tutoriales de programación, guías de instalación, todo en un único lugar."/>

    <!-- fuente de css y js -->
    <link rel="stylesheet" href="src/css/custom.css"/>
    <script src="src/js/custom.js"></script>

    <!-- protocolo open graph -->
    <meta property="og:url" content="https://zuluta.github.io"/> <!-- url a compartir -->
    <meta property="og:type" content="website"/> <!-- tipo de url a compartir -->
    <meta property="og:title" content="Documentación técnica"/> <!-- título de url a compartir -->
    <meta property="og:description" content="Documentación de proyectos, tutoriales de programación, guías de instalación, todo en un único lugar."/> <!-- descripción de url a compartir -->
    <meta property="og:image" content="https://zuluta.github.io/docs/assets/images/og.png"/> <!-- imagen de url a compartir -->
    <meta property="og:locale" content="es_ES"/>

  </head>
  
  <!-- contenido que ve el usuario -->
  <body>

    <!-- Esto mejora el rendimiento de la página, primero carga el contenido HTML y luego el código JavaScript -->
    <script src="src/js/dictionary-builder.js"></script>
  </body>

</html>
```
Lo más normal es ==colocar los scripts Javascript justo antes del cierre de la etiqueta \<body>==

<br>
<br>
