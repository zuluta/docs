---
hide:
  #- navigation
  #- toc
---


### **Cuentas necesarias**

  1. [Registrar en NPM](https://www.npmjs.com/signup){:target="_blank"}
  2. [Registrar en GitHub](https://github.com/signup){:target="_blank"}

### **Herramientas instaladas**

  1. Editor de texto ([VSCode](https://code.visualstudio.com){:target="_blank"}, Atom, Sublime Text, etc.)
  2. [Node.js](https://nodejs.org/es){:target="_blank"} (vienen con NPM)

### **Procedimiento**

1. Crea un nuevo repositorio en GitHub que se llame ==footer-js-npm==
2. Crea una carpeta en el escritorio que se llame igual a repositorio creado en GitHub ==footer-js-npm== desde la terminal
    - (==cd desktop==) Accede a la carpeta de escritorio
    - (==mkdir footer-js-npm==) Crea una carpeta llamada footer-js-npm
    - (==cd footer-js-npm==) Accede a la carpeta footer-js-npm
3. Desde el directorio ==footer-js-npm==, ejecuta el comando (==npm init==) para iniciar el proceso. Se creara un archivo ==package.json== vacío y nos pedira que rellenemos una serie de datos desde la terminal.
    - `package name: (footer-js-npm)` Escribe el nombre del paquete (dejamos por defecto) y **enter**
    - `version: (1.0.0)` ==0.1.0== Escribe la versión y **enter**
    - `description:` ==Este módulo permite generar un pie de página dinámico para aplicaciones JS con un nombre y fecha actualizado.== y  **enter**
    - `entry point: (index.js)` Escribe el nombre del archivo (dejamos por defecto) y **enter**
    - `test command:` Escribe el comando de prueba (dejamos en blanco) y **enter**
    - `git repository:` ==https://github.com/usuario/footer-js-npm== Escribe la URL del repositorio GitHub y **enter**
    - `keywords:` ==footer== Escribe palabras clave (es un metadato para NPM, no hace nada) y **enter**
    - `author:` ==Maitane Zelaieta== Escribe tu nombre y **enter**
    - `licence: (ISC)` ==MIT== Escribe una licencia (por lo general se utiliza la licencia MIT, si no se pone ninguna licencia, en terminos legales significa que nadie puede usar tu código sin que le des acceso por derechos de autor) y **enter**
    - `Is this ok? (yes)` Verificamos que todo este correcto (dejamos (yes) por defecto) y **enter**

4. Ahora si abrimos el archivo ==package.json==, veremos nuestros datos rellenados.
5. Dentro del directorio ==footer-js-npm==, creamos un archivo llamado ==index.js== con el siguiente código:

    ```js linenums="1" title="index.js"
    'use strict'; // es mas estricto con el código. finalizar con ; ya no es opcional etc.

    /*
     * Módulo JS para NPM
     * Retorna una cadena de texto en el pie de página con el copyrigth y el nombre
     */

    exports.footer = function (name) {
        return 'Copyright 2025 ' + name + ' Todos los derechos reservados';
    };
    ```

6. Dentro del directorio ==footer-js-npm==, creamos un archivo llamado ==.README.md==.
7. Dentro del directorio ==footer-js-npm==, creamos un archivo llamado ==.gitignore== y escribe lo siguiente:

    ```js linenums="1" title=".gitignore"
    node_modules
    ```

8. Desde la carpeta del proyecto ==footer-js-npm==, abre la terminal y prepara el repositorio GIT para subir al repositorio GitHub.
    - Ejecuta el comando (==git init==) Inicia el GIT
    - Ejecuta el comando (==git add .==) Agrega todos los archivos al GIT
    - Ejecuta el comando (==git commit -m "subir módulo"==) Agrega un commit al GIT
    - Ejecuta el comando (==git branch -M main==) Fuerza a renombrar la rama local actual por (main)
    - Ejecuta el comando (==git remote add origin https://github.com/usuario/footer-js-npm.git==) Agrega la url remota del repositorio GitHub
    - Ejecuta el comando (==git remote -v==) Verifica la comunicación con el repositorio remoto
    - Ejecuta el comando (==git status==) Muestra el estado de los procesos GIT
    - Ejecuta el comando (==git push -u origin main==) Sube los archivos a la rama main del repositorio GitHub

9. Entra al repositorio y verifica si se subieron bien los archivos a GitHub en la rama main.
10. Desde la carpeta del proyecto ==footer-js-npm==, abre la terminal y publica el módulo en tu cuenta NPM.
    - Ejecuta el comando (==npm publish==) Sube el módulo **footer-js-npm** a tu cuenta de NPM.
11. Entra a tu perfil de NPM y verifica que tu módulo **footer-js-npm** a sido publicado.

***

<br>
