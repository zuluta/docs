---
hide:
  #- navigation
  #- toc
---

## **¿Que es GIT?**

Git es un sistema de control de versiones distribuido que permite gestionar y seguir los cambios en el código fuente de un proyecto.

Facilita la colaboración entre desarrolladores y el mantenimiento de versiones del software.

## **Instalación y configuración inicial**

### **Instalación**

Descargar desde la web oficial: [Descargar GIT](https://git-scm.com/downloads){:target="_blank"}

### **Configurar el usuario:**

Establecer tu nombre y correo electrónico (aparecerán en los registros de commits)

>==git config --global user.name "Tu nombre"==

>==git config --global user.email "tu_email@ejemplo.com"==

### **Ver la configuración actual**

Para comprobar si se han aplicado los cambios podemos ejecutar el siguiente comando para mostrar cuál es la configuración actual de GIT:

>==git config --list==

### **Secciones principales de un repositorio git**

En un repositorio GIT podemos diferenciar las siguientes secciones:

  - Workspace
  - Staging area (Index)
  - Local repository
  - Remote repository

### **Estados de un archivo en GIT**

Un archivo puede estar en alguno de los siguientes estados:

  - ==untracked== Sin seguimiento
  - ==staged== Preparado
  - ==modified== Modificado
  - ==commited== Confirmado

Para consultar el estado de los archivos usamos el comando:


>==git status==
>
>Este comando es muy usado ya que es fundamental conocer el estado de los archivos de nuestro repositorio.

## **Trabajar con un repositorio local**

### **Creación de un repositorio local**

Un repositorio GIT es un directorio oculto llamado `.git` que se guarda en el directorio raíz de nuestro proyecto. El directorio `.git` almacena el historial de todos los cambios que se han realizado.

El comando para crear un repositorio GIT es el siguiente:

>==git init==

Por ejemplo, para crear nuestro primer repositorio podríamos hacer lo siguiente:

>==mkdir taller-git==

>==cd taller-git==

>==git init==

Si examinamos el contenido del directorio `.git` veremos el siguiente árbol de contenidos:

```
.
└── .git
    ├── HEAD
    ├── config
    ├── description
    ├── hooks
    │   ├── applypatch-msg.sample
    │   ├── commit-msg.sample
    │   ├── post-update.sample
    │   ├── pre-applypatch.sample
    │   ├── pre-commit.sample
    │   ├── pre-push.sample
    │   ├── pre-rebase.sample
    │   ├── pre-receive.sample
    │   ├── prepare-commit-msg.sample
    │   └── update.sample
    ├── info
    │   └── exclude
    ├── objects
    │   ├── info
    │   └── pack
    └── refs
        ├── heads
        └── tags
```

### **Comandos básicos para trabajar con un repositorio local**

**Paso 1**

En primer lugar comprobaremos en qué estado se encuentran los archivos del repositorio:

>==git status==

**Paso 2**

Si tenemos archivos en estado untracked o modified los añadimos a la staging area con el siguiente comando:

>==git add <\nombre_archivo>==

El comando anterior nos permite seleccionar cuáles son los archivos que queremos mover a la staging area. Si tenemos varios archivos que queremos mover a la staging area no es necesario hacerlo uno a uno, podemos usar el siguiente comando para moverlos todos a la vez:

>==git add .==

**Paso 3**

Una vez que tenemos los archivos en la staging area tenemos que hacer un commit para moverlos al repositorio:

>==git commit -m "Breve comentario con los cambios realizados"==

### **Cómo deshacer cambios**

Modificar el texto del último commit

>==git commit -m "Modifico el texto del último commit" --amend==

Añadir archivos al último commit

>==git commit --amend==

Ejemplo:

Suponemos que acabamos de hacer un commit en el repositorio pero nos hemos olvidado de añadir un archivo que queremos incluir en ese commit. En estos casos podemos utilizar el comando (==git commit --amend==) para añadir nuevos archivos al último commit realizado sobre el repositorio.

A continuación se muestra una posible secuencia de comandos simulando la situación que acabamos de describir.

>==git add archivo.txt==

>==git commit -m "Añadimos el archivo.txt"==

>==git add archivo_olvidado.txt==

>==git commit --amend==

## **Trabajar con un repositorio remoto**

Existen dos opciones para empezar a trabajar con un repositorio remoto.

  - Cuando no partimos de ningún repositorio local y lo que queremos hacer es clonar el repositorio remoto en nuestra máquina.
  - Cuando ya tenemos creado un repositorio local y queremos añadir un repositorio remoto para sincronizarnos.

**Opción 1**: Clonar un repositorio remoto

>==git clone <\url_del_repositorio_remoto>==

Ejemplo:

>==git clone https://github.com/josejuansanchez/taller-git-github.git==

Al clonar este repositorio se nos creará un directorio en nuestra máquina con el nombre `taller-git-github` con el contenido del repositorio remoto.

Esta es la opción que yo personalmente suelo utilizar a la hora de trabajar con repositorios remotos. En primer lugar creo el repositorio remoto en **GitHub** y luego hago un (==git clone==) para clonarlo en mi máquina local.

**Opción 2**: Añadir un repositorio remoto a un repositorio ya existente

>==git remote add <alias> <\url_del_repositorio_remoto>==

Ejemplo:

Suponemos que ya tenemos creado un repositorio local y queremos añadir el repositorio remoto del taller de GIT. En este caso hemos usado `taller-git` como alias. Este sería el comando que tendríamos que ejecutar:

>==git remote add taller-git https://github.com/josejuansanchez/taller-git-github.git==

Para comprobar si el repositorio remoto se ha añadido correctamente ejecutamos:

>==git remote -v==

El comando anterior nos devolverá estas dos líneas:

>==taller-git	https://github.com/josejuansanchez/taller-git-github.git (fetch)==

>==taller-git	https://github.com/josejuansanchez/taller-git-github.git (push)==

La primera línea acabada con la palabra (_fetch_) indica que esa es la url del repositorio remoto desde el que podemos recibir cambios.

La segunda línea acabada con la palabra (_push_) indica que esa es la url del repositorio remoto donde podemos enviar nuestros cambios.

### **Comandos básicos para trabajar con un repositorio remoto**

Utilizaremos los mismos comandos que usamos para trabajar con un repositorio local y además añadiremos (==git push==) y (==git pull==).

Enviamos los cambios con (==push==)

>==git push==

Usamos este comando para enviar al repositorio remoto los commits que hemos hecho en nuestro repositorio local. La forma más habitual de usarlo es hacerlo después de cada (_commit_).

```
+-------------+  +-------------+  +-------------+  +-------------+
|  Workspace  |  |   Staging   |  |    Local    |  |    Remote   |
|             |  |     Area    |  |  Repository |  |  Repository |
+------+------+  +------+------+  +------+------+  +------+------+
       |                |                |                |
       |                |                |    git push    |
       |                |                | -------------> |
       |                |                |                |
       |                |                |                |
       |                |                |                |
       |                |                |                |
       |                |                |                |
       +                +                +                +
```

Ejemplo:

>==git add archivo.txt==

>==git commit -m "Actualizamos el archivo.txt"==

>==git push==

Recibimos los cambios con (==pull==)

>==git pull==

Usamos este comando para recibir los nuevos commits que existen en el repositorio remoto y aún no tenemos en nuestro repositorio local. Además de recibir los nuevos cambios, los fusiona con el contenido de nuestro repositorio local, actualizando de este modo los archivos que tengamos en la sección `Local Repository`.


```
+-------------+  +-------------+  +-------------+  +-------------+
|  Workspace  |  |   Staging   |  |    Local    |  |    Remote   |
|             |  |     Area    |  |  Repository |  |  Repository |
+------+------+  +------+------+  +------+------+  +------+------+
       |                |                |                |
       |                |                |    git pull    |
       |                |                | <------------- |
       |                |                |                |
       |                |                |                |
       |                |                |                |
       |                |                |                |
       |                |                |                |
       +                +                +                +
```

## **El archivo `.gitignore`**

Dentro del directorio raíz de nuestro proyecto podemos tener un archivo especial llamado `.gitignore` donde indicamos los archivos, tipos de archivos o carpetas que queremos que sean ignorados por GIT.

Por ejemplo, si en nuestro repositorio no queremos guardar archivos o carpetas, tendríamos el siguiente contenido en el archivo `.gitignore`:

>Las extensiones deben llevar un (==*==) delante.

>Las carpetas deben llevar una (==/==) delante.

>Ejemplo de extensiones, archivos y carpeta excluidos del GIT:
```linenums="1" title=".gitignore" 
*.class
*.log
*.html
archivo_para_ignorar.html
archivo_para_ignorar.css
archivo_para_ignorar.js
/carpeta_para_ignorar
```

***

### Fuentes:

>Sitio web oficial: [GIT](https://git-scm.com){:target="_blank"}

***

<br>
