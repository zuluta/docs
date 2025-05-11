---
hide:
  #- navigation
  #- toc
---

## **¿Qué es Visual Studio Code?**

Visual Studio Code, al que conocemos también como **VSCode**, es un editor de código para programadores gratuito, de código abierto y multiplataforma desarrollado por Microsoft.

Básicamente, se trata de un editor de código. Esto quiere decir, una herramienta que nos permite editar el texto plano de los archivos de código para programación. Sin embargo, detrás de esa necesidad inicial, Visual Studio Code se puede configurar para realizar muchos tipos de tareas, incluso más allá de abrir y escribir simples archivos de texto.

### **Ventajas:**

  1. Eficiencia y agilidad en la programación.
  2. Amplia compatibilidad con lenguajes y frameworks.
  3. Potentes herramientas de depuración y pruebas.
  4. Integración nativa con Git y control de versiones.
  5. Personalización y extensibilidad para adaptarse a tus necesidades.

## **Instalación y configuración de VSCode**

Para instalar el editor, es importante acudir a la página oficial de [VSCode](https://code.visualstudio.com){:target="_blank"}. Allí encontraremos el instalador para Windows, macOS y Linux, aunque en el sistema del pingüino también es posible instalarlo a través de algunos gestores de software de las distribuciones.

Una vez instalado, ya tenemos lo suficiente para trabajar con muchos lenguajes y con unas personalizaciones que se adaptan a la mayoría de los gustos. Sin embargo, puedes configurar ajustes básicos como el tema y las preferencias de usuario desde la sección de «Ajustes» accesible mediante el menú superior.

## **Selección y uso de extensiones relevantes**
Si trabajamos con un lenguaje o framework en particular, luego sería bueno localizar las extensiones que nos permitan mejorar la experiencia de desarrollo. 

En la parte de la izquierda hay un botón para buscar extensiones o administrar las que ya tengamos instaladas. El ecosistema de extensiones de VS Code es enorme, como podrás comprobar.

Es importante seleccionar y utilizar extensiones relevantes para tus necesidades. Además, recomendamos instalarlas poco a poco, de manera que podamos familiarizarnos con ellas de una en una en lugar de instalar de manera aleatoria extensiones que quizás no lleguemos a usar nunca.

***

## **VSCode, Extensiones JavaScript para Aumentar la Productividad**

En el desarrollo de JavaScript, disponer de las herramientas adecuadas puede mejorar significativamente tu productividad y la calidad del código. Aquí tienes algunas que pueden ayudarte:

  1. [Lodash :octicons-link-external-24:](https://lodash.com/){:target="_blank"}
  2. [Quokka.js :octicons-link-external-24:](https://quokkajs.com/){:target="_blank"}
  3. [ESLint :octicons-link-external-24:](https://es.eslint.org/play/){:target="_blank"}

### **1. Lodash:**

Lodash es una librería de JavaScript ampliamente utilizada por los desarrolladores debido a sus numerosas funciones útiles para manipular objetos, arrays y números. Durante mucho tiempo, Lodash ha sido una herramienta imprescindible en muchos proyectos, facilitando la resolución de problemas complejos.

Sin embargo, con la evolución constante de JavaScript, muchas de las funciones que antes requerían de Lodash, ahora se pueden realizar con código JavaScript nativo.

Sin embargo, es importante tener en cuenta que Lodash sigue siendo una biblioteca muy útil y con una gran cantidad de funciones que aún no han sido incorporadas a JavaScript. Por lo tanto, si aún necesitas alguna de estas funciones, Lodash sigue siendo una excelente opción.

### **2. Quokka.js:**

Quokka.js es un bloc de notas en tiempo real para JavaScript que ofrece información y resultados de ejecución en tiempo real mientras escribes. Esta extensión puede acelerar significativamente tu flujo de trabajo de desarrollo.

**Funciones:**

  - valúa tu código JavaScript mientras escribes, mostrando los resultados instantáneamente dentro del editor VS Code.
  - Proporciona anotaciones inline para indicar la salida y los valores de las variables, facilitando la comprensión del comportamiento del código.
  - Ofrece información sobre las expresiones, permitiéndote ver los resultados y efectos de cada línea de código, lo que ayuda a depurar y solucionar problemas.
  - Te permite registrar valores y mostrarlos en el editor, proporcionando una visibilidad adicional del flujo de ejecución del código.

### **3. ESLint:**

ESLint es un linter ampliamente adoptado que te ayuda a detectar errores, hacer cumplir las normas de programación y mejorar la calidad del código en JavaScript y TypeScript.

**Funciones:**

  - Proporciona información instantánea y resalta los problemas de código mientras escribes.
  - Te permite personalizar sus reglas en función de los requisitos específicos de tu proyecto, garantizando la coherencia en toda tu base de código.
  - Detecta errores, pero también puede corregir automáticamente ciertos problemas, como la sangría y el espaciado, ayudándote a mantener un código limpio y bien formateado.
  - Admite el uso de plugins y reglas personalizadas, lo que te permite adaptarlo a las necesidades únicas de tu proyecto.

***

## **¿Cómo funciona el debugger?**

En JavaScript, disponemos de una herramienta que se llama el debugger. El debugger, también conocido como una herramienta de depuración, sirve para encontrar fallos en nuestro código de forma más eficiente. Dicho de otra manera, el debugger es una herramienta que nos ayuda a inspeccionar el código de nuestro archivo.

Para depurar un código es usando una palabra reservada en JS llamada debugger. Esta sentencia lo que nos permite es especificar en el código la línea exacta donde queremos que se detenga nuestra aplicación web para ser depurada.

El siguiente ejemplo muestra un bloque de código donde ha sido insertada una sentencia debugger, para invocar el depurador (si existe) cuando la función es ejecutada.

```js linenums="1" title="javascript"
function codigoPotencialmenteDefectuoso() {
  debugger;
  // realizar paso a paso o examinar código que contiene
  // potenciales errores
}
```

Otro ejemplo:

```js linenums="1" title="javascript"
const number = parseInt(prompt('Ingresa un número (del 1 al 10):'));
const randomNumber = Math.floor(Math.random() * 10);

debugger;
if (randomNumber === number) {
    console.log('Adivinaste!');
} else {
    console.log(`Perdiste! El número es ${randomNumber}`);
}
```

Cuando el depurador es invocado, la ejecución se detiene en la sentencia debugger. Es como un punto de interrupción en el script.

***

<br>
