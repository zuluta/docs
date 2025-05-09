---
hide:
  #- navigation
  #- toc
---

Los módulos en JavaScript son fundamentales para organizar y estructurar código de manera eficiente en aplicaciones modernas. Dividir el código en módulos permite gestionar funcionalidades específicas de forma independiente, facilitando el mantenimiento, la escalabilidad y la colaboración en equipos de desarrollo.

## **¿Qué son los módulos en JavaScript?**

Un módulo en JavaScript es un archivo que contiene código reutilizable como variables, funciones o [clases](../clases/). Al usar módulos, puedes separar la lógica en fragmentos manejables que pueden importarse y exportarse entre archivos. Esto mejora la organización del código y evita conflictos al proporcionar un ámbito privado para cada módulo.

Antes de la introducción de los módulos ES6, se usaban sistemas como CommonJS (Node.js) y AMD (navegadores) para manejar la modularidad. Los módulos ES6 estandarizan esta funcionalidad y son compatibles con navegadores modernos.

Los módulos permiten:

  - **Reutilización**: Puedes compartir y reutilizar funcionalidades en diferentes partes de tu aplicación.
  - **Encapsulación**: Las variables y funciones de un módulo están protegidas en su propio ámbito.
  - **Carga optimizada**: Los módulos se cargan de forma asíncrona, mejorando el rendimiento de la aplicación.

## **Exportar código**

Para que un módulo comparta funcionalidades, debes usar la palabra clave `export`. Hay dos tipos principales de exportaciones:

  1. **Exportación nombrada**: Permite exportar múltiples elementos desde un módulo, y cada elemento debe ser importado usando su nombre exacto.

```js linenums="1" title="javascript"
// archivo.js
export const PI = 3.1416;

export function calcularArea(radio) {
    return PI * radio * radio;
}
```

  2. **Exportación por defecto**: Permite exportar un solo elemento como predeterminado, lo que simplifica su importación.

```js linenums="1" title="javascript"
// archivo.js
export default function saludo() {
    return "Hola, Módulos!";
}
```

## **Importar código**

La palabra clave `import` se utiliza para traer funcionalidades de otros módulos. Puedes importar elementos específicos (exportación nombrada) o el elemento principal (exportación por defecto).

```js linenums="1" title="javascript"
// importar.js
import saludo from './archivo.js'; // Exportación por defecto
import { PI, calcularArea } from './archivo.js'; // Exportación nombrada

saludo(); // "Hola, Módulos!"
calcularArea(5); // 78.54
```

## **Configuración básica en HTML**

Para usar módulos en un entorno web es necesario configurar correctamente los archivos HTML para que el navegador pueda interpretar las importaciones y exportaciones. Esto se logra utilizando el atributo `type="module"` en la etiqueta `<script>`.

```html linenums="1" title="html"
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Módulos en JavaScript</title>
</head>
<body>
  <!--contenido -->
  <!--contenido -->
  <script type="module" src="app.js"></script>
</body>
</html>
```

**Notas Importantes:**

  - **Origen seguro**: Los módulos deben servirse desde un servidor HTTP o HTTPS. Si intentas cargarlos localmente (con `file://`), navegadores como Chrome bloquearán las importaciones.
  - **Compatibilidad**: Los módulos ES6 son compatibles con la mayoría de los navegadores modernos, pero es recomendable verificar el soporte en los navegadores objetivo.

## **Características clave de los módulos en JavaScript**

  1. **Modo estricto por defecto**: Los módulos se ejecutan automáticamente en strict mode, ayudando a evitar errores comunes.
  2. **Ámbito privado**: Las variables y funciones declaradas en un módulo no son accesibles fuera de él, a menos que se exporten explícitamente.
  3. **Carga diferida**: Los módulos se cargan de manera asíncrona y solo cuando son necesarios, mejorando el rendimiento.

Como mencionamos anteriormente, cada módulo en JavaScript tiene su propio ámbito, lo que significa que las variables, funciones y clases definidas en un módulo no son visibles fuera de él a menos que se exporten. Esto ayuda a mantener un código más seguro y a evitar conflictos de nombres.

```js linenums="1" title="javascript"
// archivo.js
const secreto = "Esto es privado";
export const publico = "Esto es público";
```

En este caso, la variable `secreto` no es accesible desde otros archivos, ya que no se exporta.

## **Beneficios de usar módulos**

Los módulos aportan varias ventajas significativas al desarrollo de aplicaciones en JavaScript:

  1. **Estructura clara y organizada**: Al dividir tu aplicación en módulos, cada archivo puede enfocarse en una funcionalidad específica, como manejar usuarios o interactuar con una API.
  2. **Prevención de conflictos de nombres**: Las variables y funciones en un módulo no interfieren con las de otros archivos.
  3. **Reutilización de código**: Puedes importar funciones, objetos o clases en cualquier parte de tu aplicación o incluso entre proyectos.
  4. **Escalabilidad**: Los módulos facilitan el trabajo en equipo al permitir que varios desarrolladores trabajen en diferentes partes de la aplicación sin interferencias.

## **Restricciones de los módulos en JavaScript**

Aunque los módulos son muy útiles, tienen algunas limitaciones:

  - **Origen seguro**: Deben cargarse desde un servidor.
  - Extensión `.mjs` en Node.js: Aunque los módulos ES6 funcionan en Node.js, es común usar la extensión `.mjs` para diferenciarlos de los módulos CommonJS.
  - Una sola exportación por defecto: Un módulo puede tener solo una exportación por defecto, aunque puede incluir múltiples exportaciones nombradas.

## **Buenas prácticas al trabajar con módulos**

  - **Nombra tus módulos descriptivamente**: Usa nombres que reflejen claramente el propósito del módulo.
  - **Organiza por funcionalidades**: Divide tu código en módulos basados en áreas específicas, como `usuarios.js` o `productos.js`.
  - **Usa exportaciones por defecto para componentes principales**: Exporta como predeterminada la funcionalidad más importante del módulo y usa exportaciones nombradas para elementos secundarios.
  - **Evita dependencias circulares**: Diseña tus módulos para que no se necesiten entre sí de manera circular, ya que esto puede causar errores.

***

### **Conclusión**

Los módulos en JavaScript son esenciales para estructurar y organizar código en aplicaciones modernas. Gracias a las exportaciones e importaciones, puedes crear proyectos modulares y escalables con facilidad. Su capacidad de encapsulación y su compatibilidad con navegadores modernos los convierten en una herramienta indispensable para cualquier desarrollador.

En el siguiente artículo profundizaremos en [Exportación en JavaScript](../exportacion-modulos/), donde exploraremos cómo exportar variables, funciones y clases de un módulo para que sean accesibles en otros archivos.

***

<br>
