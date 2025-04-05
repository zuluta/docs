---
hide:
  #- navigation
  - toc
---

# Despliegue de proyecto local a GitHub Pages

<p><strong>01.</strong> Accede a GitHub y crea un repositorio nuevo.</p>

![Git Hub Image](images/gh_deploy/01.nuevo_repo_github.png)
<br>
<br>

<p><strong>02.</strong> Escribe el mismo nombre del proyecto local, deja en público y pulsa el botón crear repositorio.</p>

![Git Hub Image](images/gh_deploy/02.crear_repo_github.png)
<br>
<br>

<p><strong>03.</strong> Muestra los comandos y la URL remota del repositorio creado.</p>

![Git Hub Image](images/gh_deploy/03.codigo_repo_terminal.png)
<br>
<br>

<p><strong>04.</strong> Comandos para sincrinizar por primera vez GIT con GitHub desde la terminal de VSCode.</p>

  - `git init` Inicia el Git
  - `git config --global user.name "Your_Name"` Usuario de github
  - `git config --global user.email "you@example.com"` Email de github
<br>

<p><strong>05.</strong> Comandos de terminal mas utilizados en GIT.</p>

  - `git init` Inicia el Git
  - `git add .` Agrega todos los archivos al Git
  - `git add ejemplo.html` Agrega el archivo indibidualmente al Git
  - `git commit -m 'inserta el mensaje aqui'` Agrega un commit al Git
  - `git branch -M main` Cambia a la rama main
  - `git remote add origin https://github.com/usuario/mi_repositorio.git` Agrega la url remota del repositorio github
  - `git remote -v` Verifica la comunicación con el repositorio remoto
  - `git status` Muestra el estado de los procesos Git
  - `git push -u origin main` Sube los archivos a la rama main del repositorio github

!!! info "El orden de ejecución"

    El orden de ejecución, variara en función de lo que quieras hacer. Por lógica, primero se inicia el Git, se agregan los archivos, se envia un commit, la verificación de estado y la comunicación con el repositorio solo nos da información, no hace ningun cambio en el repositorio.
<br>

<p><strong>06.</strong> Entra en VSCode y abre una terminal nueva.</p>
  - Desde la carpeta de trabajo "proyecto_docs", activa el entorno virtual (.\env\scripts\activate).
  - Accede a la carpeta del proyecto "docs" y lanza el comando "mkdocs build" para compilar. Se creara una nueva carpeta llamada "site" donde sera compilado todo el proyecto.

![Git Hub Image](images/gh_deploy/04.build_proyecto_docs.png)
<br>
<br>

<p><strong>07.</strong> Desde la carpeta del proyecto "docs", abre la terminal y prepara el repositorio GIT para subir al repositorio GitHub.</p>
  - Ejecuta el comando (git init)
  - Ejecuta el comando (git add .)
  - Ejecuta el comando (git commit -m "despliegue")
  - Ejecuta el comando (git branch -M main)
  - Ejecuta el comando (git remote add origin https://github.com/zuluta/docs.git)
  - Ejecuta el comando (git remote -v)
  - Ejecuta el comando (git status)
  - Ejecuta el comando (git push -u origin main)

<br>
<br>

<p><strong>08.</strong> Entra al repositorio y verifica si se subieron bien los archivos a GitHub en la rama main.</p>

![Git Hub Image](images/gh_deploy/05.verificar_subida_github.png)
<br>
<br>

<p><strong>09.</strong> GitHub permite crear una pagina web gratis desde el repositorio. Ejecuta el comando (mkdocs gh-deploy), este comando es específico de mkdocs para GitHub. Este comando creara de forma automática una nueva rama "gh_pages" en el mismo repositorio del proyecto para poder desplegar GitHub Pages.</p>

<p><strong>10.</strong> Entra al repositorio de GitHub y verifica si se creo la rama "gh-pages".</p>

![Git Hub Image](images/gh_deploy/06.crear_rama_gh_pages.png)
<br>
<br>

<p><strong>11.</strong> Entra en Settings, luego en Pages, donde pone Branch, selecciona la rama "gh-pages" y la carpeta "(root)". Pulsa el botón de guardar y espera unos segundos a que se active la página.</p>

![Git Hub Image](images/gh_deploy/07.selec_repo_pages.png)
<br>
<br>

<p><strong>12.</strong> Entra en Settings, luego en Pages, donde pone GitHub Pages, verifica que la página este operativa.</p>

![Git Hub Image](images/gh_deploy/08.visitar_pagina.png)
<br>
<br>

<p><strong>13.</strong> Para actualizar GitHub Pages, primero ejecuta (git push -u origin main) al repositorio del proyecto en la rama "main" y luego (mkdocs gh-deploy) para la rama "gh-pages". verifica los cambios en la página.</p>
<br>
<br>
