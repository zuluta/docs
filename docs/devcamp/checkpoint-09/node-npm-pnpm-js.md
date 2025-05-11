---
hide:
  #- navigation
  #- toc
---

## **¿Que es Node.js?**

**[Node.js](https://nodejs.org/es){:target="_blank"} es un entorno de ejecución de JavaScript multiplataforma**, de código abierto y gratuito que permite a los desarrolladores crear servidores, aplicaciones web, herramientas de línea de comando y scripts.

Un error común entre los desarrolladores es que Node.js es un framework de backend y que sólo se utiliza para construir servidores. 
Esto no es cierto: **Node.js puede utilizarse tanto en el frontend como en el backend**.

**Node.js no es**:

  - No es un lenguaje de programación
  - No es un framework
  - No es una web
  - No no es un servidor
  - No no es un hosting

### **Instalar Node.js en Windows**

Descargue el instalador de Windows **NodeJS en su versión LTS** (_recomendada_) directamente desde el sitio web oficial [nodejs.org](https://nodejs.org/es){:target="_blank"}. Ejecuta el instalador y dale a todo siguiente hasta finalizar la instalación, no hace falta cambiar nada.

### **Verifica la versión de Node.js instalada**

En la sección anterior, hemos instalado con éxito Node. **Vamos a verificar la versión instalada**. Ejecuta el siguiente comando en la terminal.

```bash
node -v
```

También puede comprobarlo a través de código más largo

```bash
node --version
```

Debería ver una salida similar a esta. Aunque el número de versión puede variar.

```bash
v22.15.0
```

***

## **¿Que es NPM?**

**NPM** es el **gestor de paquetes predeterminado de Node.js**. Es decir, NPM normalmente no se instala de forma aislada, si no que **se instala como un componente al instalar Node.js**.

Por tanto, antes de poder utilizar NPM, lo primero es asegurarnos de **tener correctamente instalado Node.js** en nuestro sistema.

### **Actualizar NPM globalmente**

Este comando instalará la última versión estable (LTS = Long Time Support) sobre la versión actual, y hace que este disponible en la consola de comando desde cualquier ubicación.

```bash
npm install -g npm@lts
```

***

## **Alternativas a NPM**

Existen algunas alternativas a NPM que añaden características y/o permiten realizar las mismas tareas de NPM pero de una forma alternativa que ofrece ciertas ventajas. Entre estas alternativas podemos encontrar:

  1. **[PNPM](https://pnpm.io/es/){:target="_blank"}**:	Alternativa rápida que hace uso eficiente del espacio en disco.

### **¿Por qué PNPM en lugar de NPM?**

Utilizar **pnpm** como alternativa a **npm** es una muy buena opción por muchas razones, ya que puedes gestionar versiones de Node, instalar y gestionar paquetes y dependencias, entre otras varias ventajas.

Pero sin duda, una de las mejores, es que pnpm utiliza una forma alternativa de instalación de paquetes, donde se gestionan mediante un almacén compartido, ahorrando espacio en disco y realizando una instalación de paquetes mucho más rápida:

<br>

![Image](../../assets/images/devcamp/checkpoint-09/npm-vs-pnpm.png)

<br>

Si lo deseas, puedes utilizar **npm**, pero si utilizas **pnpm** aprovecharás varias ventajas y funcionalidades de este último que mejorarán tu experiencia como desarrollador.

### **Instalar PNPM con Corepack** (experimental)

Esto instalará automaticamente pnpm en tu ordenador mediante Corepack. Ejecuta el siguiente comando:

```bash
corepack enable pnpm
```

### **Instalar PNPM con NPM** (recomendado)

Si tienes Node.js instalado en tu ordenador, es agregarlo como un paquete global mediante NPM. ejecuta el siguiente comando:

> **Esto instalará PNPM de forma global en tu ordenador** (lo que significa que podrás utilizarlo en cualquier proyecto de Node.js).

```bash
npm install -g pnpm
```

### **Actualizar PNPM con PNPM**
Si tienes PNPM instalado, puedes actualizar PNPM a su última versión o una vesión específica, ejecuta el siguiente comando:

```bash
pnpm self-update # actualiza pnpm a su última versión.
pnpm self-update 9.6.5 # actualiza pnpm a una versión específica.
```

### **Verifica la versión de NPNM instalada**

Para asegurarte de que la instalación se realizó correctamente, puedes verificar la versión de PNPM que tenemos instalada con el siguiente comando.

```bash
pnpm --version
```

Deberías ver la versión de PNPM instalada. Por ejemplo, algo así.

```bash
9.15.0
```

***

## **Instalar paquetes con NPM**

Cuando instalas Node.js, NPM se instala automáticamente junto con él. Hemos cubierto cómo instalar Node.js en las secciones anteriores, así que ahora vamos a echar un vistazo al comando para instalar un paquete con NPM:

```bash
npm install nombre_del_paquete
```

Sí, es así de fácil. Incluso puedes instalar varios paquetes a la vez:

```bash
npm install pkg-1 pkg-2 pkg-3
```

instala y **guarda el nombre del paquete en la lista** de `dependencies` dentro del archivo **package.json**, con el siguiente comando:

```bash
npm install --save nombre_del_paquete
```

instala pero no **guarda el nombre del paquete en la lista** de `dependencies` dentro del archivo **package.json**, con el siguiente comando:

```bash
npm install --no-save nombre_del_paquete
```

instala y **guarda el nombre del paquete en la lista** de `devDependencies` dentro del archivo **package.json**, con el siguiente comando:

```bash
npm install --save-dev nombre_del_paquete
```

### **Actualizar paquetes con NPM**

Con el siguiente comando, **npm** actualizara todos los paquetes a la última versión.
```bash
npm update
```

Puede especificar el paquete que quieras actualizar con el siguiente comando:

```bash
npm update nombre_del_paquete
```

### **¿Qué son las instalaciones globales de NPM?**

Las instalaciones globales en NPM se refieren a la instalación de paquetes de manera global en tu sistema. Esto significa que los paquetes estarán disponibles en cualquier proyecto de JavaScript que trabajes en tu máquina, en lugar de estar restringidos a un proyecto específico.

**Instalar paquetes de forma global** en NPM es muy sencillo. Esto te permite utilizar el paquete en cualquier lugar de tu máquina. Solo necesitas ejecutar el siguiente comando en tu terminal:

```bash
npm install -g nombre_del_paquete
```

**puedes desinstalar paquetes globales** en NPM utilizando el siguiente comando:

```bash
npm uninstall -g nombre_del_paquete
```

**Muestra todos los paquetes instalados de forma global** con el siguiente comando:

```bash
npm list -g --depth=0
```

***

## **Instalar paquetes con PNPM**

Una vez que PNPM esté instalado en tu sistema puedes utilizarlo para gestionar los paquetes de tu proyecto de Node.js de la misma manera que lo harías con NPM

  - (==pnpm install==) Instala las dependencias del proyecto.
  - (==pnpm add nombre_del_paquete==) Agrega un nuevo paquete al proyecto.
  - (==pnpm remove nombre_del_paquete==) Elimina un paquete del proyecto.

***

## **Instalar dependencias con NPM**

La función principal de **NPM** es instalar y gestionar las dependencias de nuestro proyecto. Para ello, como sabemos, registra las dependencias en el fichero **package.json**.

Estas dependencias están organizadas en dos categorías:

  1. `Dependencies`: Dependencias requeridas para la ejecución
  2. `DevDependencies`: Dependencias necesarias solo durante el desarrollo

Si tenemos nuestras dependencias correctamente configurados en el archivo **package.json**, podemos instalarlas simplemente con el siguiente comando:

```bash
npm install
```

Este comando leerá el archivo **package.json** y descargará todas las dependencias especificadas en la sección `dependencies`. Estas dependencias se almacenarán en una carpeta llamada **node_modules** en el directorio del proyecto.

Esto es muy habitual **cuando bajamos un proyecto Open Source**. Al publicar un proyecto, este se guarda en los repositorios (como Github) sin las librerías. Esto es lógico, es para ahorrar espacio.

**Es un error muy frecuente**, al principio, descargar un proyecto Open Source y pensar que no funciona. En muchas ocasiones es, simplemente, que nos hemos olvidado de instalar las dependencias con este comando.

><br>
> **Nota**: Si estas trabajando con GIT, es importante ignorar la carpeta **node_modules**, para ello, crea un archivo llamado (==.gitignore==) y agrega el nombre de la carpeta en una nueva línea. Esto es para cuando agamos (==git add .==) no nos incluya las librerias que contiene esa carpeta a GIT ni tampoco nos suba esos archivos a GitHub cuando agamos un `push` ya que es una carpeta muy pesada y no necesitamos en GIT. Es solo para tenerlo en cuenta. **Las carpetas deben llevar una** (==/==) **delante**.
>
>
> **Ejemplo de carpeta y archivos excluidos del GIT**:
>
> ``` linenums="1" title=".gitignore"
> archivo_para_ignorar.html
> archivo_para_ignorar.css
> archivo_para_ignorar.js
> /node_modules
> ```
><br>

### **Instalar dependencias requeridas (`dependencies`)**

Cuando se ejecuta (==npm install==) sin ninguna opción adicional, NPM instalará las dependencias que se encuentran bajo la sección `dependencies` en el archivo **package.json**. Estas son las dependencias necesarias para que la aplicación funcione correctamente en un entorno de producción.

Supongamos que tenemos un fichero **package.json** como el siguiente:

```json
{
  "name": "mi-proyecto",
  "version": "1.0.0",
  "dependencies": {
    "express": "^4.17.1",
    "lodash": "^4.17.21"
  }
}
```

En este caso, (==npm install==) descargará e instalará las versiones más recientes de las bibliotecas **express** y **lodash**.

### **Instalar dependencias de desarrollo (`devDependencies`)**

Si deseamos instalar las dependencias necesarias para el desarrollo del proyecto (como pruebas unitarias, herramientas de compilación o pruebas de estilo de código), debemos usar la opción (==--dev==) o su forma corta (==-D==). Por ejemplo:

```bash
npm install --dev
```

```bash
npm install -D
```

Esto instalará todas las dependencias que se encuentran en la sección `devDependencies` de nuestro archivo **package.json**. Recordemos que **estas dependencias no se incluirán en el paquete final** cuando distribuyamos nuestra aplicación.

***

## **Qué es el fichero Package.json de NPM**

El fichero **package.json** es un componente esencial dentro del funcionamiento de **NPM**. Este archivo desempeña un papel fundamental ya que almacena los datos del proyecto proyecto, sus dependencias, scripts personalizados y metadatos importantes.

**Entre las funciones que tiene este fichero está:**

  - **Gestión de dependencias**: El uso de package.json permite gestionar las dependencias del proyecto

  - **Reproductibilidad**: La combinación del fichero package.json junto con el fichero package-lock.json asegura que si puedes reproducir un proyecto (por ejemplo para duplicar, copiar a otra máquina)

  - **Colaboración y distribución**: Para compartir un paquete con otros desarrolladores, simplemente proporcionar el fichero package.json y los comandos para instalar las dependencias será suficiente

### **Estructura básica de package.json**

La estructura del fichero **package.json** es un formato **JSON** (_JavaScript Object Notation_). Por lo que es muy fácil de entender por una persona, e incluso editarlo a mano sin demasiada dificultad.

El fichero **package.json** consta de varias claves y valores que definen las características y dependencias del proyecto. Veamos un ejemplo sencillo de un posible archivo **package.json**:

```json
{
  "name": "curso-npm",
  "version": "1.0.0",
  "description": "Curso de NPM - Aprende a utilizar Node Package Manager",
  "main": "index.js",
  "author": "Nerea Zelaieta",
  "license": "MIT",
  "scripts": {
    "start": "node index.js",
    "test": "echo \"No hay pruebas disponibles\""
  },
  "dependencies": {
    "express": "^4.17.1",
    "lodash": "^4.17.21"
  },
  "devDependencies": {
    "nodemon": "^2.0.12",
    "eslint": "^7.32.0"
  }
}
```

**Descripción**:

  - `name`:	Nombre del proyecto.	(=="curso-npm"==)
  - `version`:	Versión del proyecto.	(=="1.0.0"==)
  - `description`:	Descripción breve del proyecto.	(=="Curso de NPM - Aprende a utilizar Node Package Manager"==)
  - `main`:	Archivo principal del proyecto, es el punto de entrada cuando se importa el módulo.	(=="index.js"==)
  - `author`:	Nombre del autor del proyecto. (=="Nerea Zelaieta"==)
  - `license`:	Licencia del proyecto.	(=="MIT"==)
  - `scripts`:	Define comandos que se pueden ejecutar usando npm run script-name.
  - `dependencies`:	Lista de dependencias requeridas para que el proyecto funcione correctamente en producción.	(=="express"==), (=="lodash"==)
  - `devDependencies`:	Lista de dependencias requeridas solo para desarrollo.	(=="nodemon"==), (=="eslint"==)

### **Dependencies y DevDependencies**

Las claves `dependencies` y `devDependencies` enumeran las dependencias del proyecto. La diferencia entre una y otra es que

  1. `dependencies` son necesarias para que el programa funcione correctamente en producción.
  2. `devDependencies` son solo requeridas durante el desarrollo.

**Separar estas dependencias es importante** para permitir usar herramientas solo en la fase de desarrollo, pero evitando que se incluyan paquetes innecesarios en la distribución de la aplicación final.

Por ejemplo, **imagina que estás usando una librería que te ayuda durante el desarrollo remarcándote errores de sintaxis**. **No quieres que esa librería forme parte del producto final**. En ese caso, la añadirías en `devDependencies`.

***

## **Qué es el fichero Package-lock.json de NPM**

El fichero **package-lock.json** es un fichero que **se genera automáticamente por NPM** en operaciones donde modifica el árbol de node_modules o el archivo **package.json**.

**Su función principal es describir el árbol de dependencias exacto que se generó durante una instalación**, permitiendo que futuras instalaciones generen árboles idénticos, independientemente de las actualizaciones intermedias de las dependencias.

**No debemos tocar a mano el fichero Package-lock, es un fichero interno usado por NPM**. Simplemente **acostúmbrate a ignorarlo**.

***

<br>
