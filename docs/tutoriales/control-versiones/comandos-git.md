---
hide:
  #- navigation
  - toc
---

# GIT desde la línea de comandos

### Comandos básicos para trabajar en localhost:

  - ==git init== Iniciar GIT
  - ==git add .== Agrega todos los archivos al GIT
  - ==git commit -m "primer commit"== Agrega un commit al GIT

### Comandos para sincrinizar por primera vez GIT con GitHub desde terminal de VSCode:

  - ==git init== Iniciar GIT
  - ==git config --global user.name "nombre_usuario"== Usuario de GitHub
  - ==git config --global user.email "micorreo@ejemplo.com"== Email de GitHub

### Comandos basicos para subir nuestro proyecto localhost al repositorio de GitHub:

  - ==git init== Iniciar GIT
  - ==git add .== Agrega todos los archivos al GIT
  - ==git commit -m "primer commit"== Agrega un commit al GIT
  - ==git branch -M main== Fuerza a renombrar la rama local actual por (main) {~~actual~> main~~}
  - ==git remote add origin https://github.com/usuario/mi_repositorio.git== Crea una conexión remota llamada {++origin++} con el repositorio de GitHub
  - ==git remote -v== Verifica la comunicación con el repositorio remoto
  - ==git status== Muestra el estado de los procesos GIT
  - ==git push -u origin main== Sube los archivos a la rama main remoto de GitHub

### Comandos útiles:

  - ==git status== Muestra el estado de los procesos GIT
  - ==git add ejemplo.html== Agrega los archivos indibidualmente al GIT
  - ==git remote -v== Verifica la comunicación con el repositorio remoto
  - ==git log== Muestra el histórico de commits
  - ==git log -n 2== Muestra los últimos 2 commits
  - ==git log prueba.html== Muestra los commits del archivo (prueba.html)
  - ==git switch main== Cambia de la rama actual a la rama (main)
  - ==git branch branch-test== Crea una nueva rama (branch-test) a partir de la rama actual
  - ==git branch -m branch-test== Renombra la rama local actual por (branch-test) {~~actual~> branch-test~~}
  - ==git branch -M branch-test== Fuerza a renombrar la rama local actual por (branch-test) {~~actual~> branch-test~~}
  - ==git branch== Muestra todas las ramas locales y distingue con un (*) la rama actual
  - ==git branch --list== Muestra todas las ramas locales y distingue con un (*) la rama actual
  - ==git branch -r== Muestra todas las ramas del repositorio remoto
  - ==git branch -a== Muestra todas las ramas, tanto locales como remotas y distingue con un (*) la rama actual
  - ==git branch --show-current== Muestra la rama actual
  - ==git branch -d branch-test== Elimina la rama (branch-test) del repositorio local si esta fusionado con (main)
  - ==git branch -D branch-test== Fuerza a eliminar la rama (branch-test) del repositorio local este o no fusionado con (main)
  - ==git branch --no-merged== Muestra las ramas que estan sin fusionar con (main)
  - ==git remote add origin https://github.com/usuario/mi_repositorio.git== Crea una conexión remota llamada {++origin++} con el repositorio de GitHub
  - ==git clone https://github.com/usuario/mi_repositorio.git== Copia el repositorio remoto completo al local y se crea automáticamente una conexión remota llamada {++origin++}
  - ==git pull origin main== Actualiza la rama actual del repositorio local con los nuevos cambios efectuados en la rama (main) del repositorio remoto
  - ==git merge branch-test== Fusiona la rama (branch-test) a la rama actual del repositorio local
  - ==git push origin --delete branch-test== Elimina la rama (branch-test) del repositorio remoto
  - ==git fetch --prune== Elimina todas las referencias de seguimiento obsoletas del repositorio remoto
  - ==git prune== Elimina todas las referencias de seguimiento obsoletas del repositorio local
  - ==git prune --verbose== Elimina y muestra todas las referencias de seguimiento obsoletas que a eliminado del repositorio local
  - ==git commit --amend -m "texto corregido"== Edita el commit mas reciente y lo sustituye por uno nuevo

### Comandos para restaurar o resetear a un commit anterior específico:

  1. El método (git restore): 

    - ==git log --oneline== Muestra información simplificada de commits donde sale el hash de cada uno
    - ==git restore --source 20cf9cb prueba.html== Restaura el archivo (prueba.html) al commit mediante hash (20cf9cb)

  2. El método (git reset):

    - ==git log --oneline== Muestra información simplificada de commits donde sale el hash de cada uno
    - ==git reset 20cf9cb== Regresa al commit mediante hash (20cf9cb)

    !!! info "NOTA"
        A pesar de que los commits ya no aparecen en el log, no se eliminan de GIT
<br>

!!! info "NOTA"
    - Para detener el servidor de "mkdocs" pulsa (ctrl + c)
    - Para limpiar la consola utiliza el comando (==cls==) o (==clear==)
    - Para salir de algun comando GIT pulsa (q)

!!! failure "MALAS PRÁCTICAS"
    Está totalmente desaconsejado alterar el historial de commits, esto podria generar conflictos con los commits del repositorio remoto cuando se vaya hacer push o pull por cualquiera de los miembros, intenta siempre trabajar hacia adelante. Por lo general, está bien hacer este tipo de cambios en su propio repositorio local.

!!! success "BUENAS PRÁCTICAS"
    El mensaje del commit se escribe en presente, debe ser corto y conciso, no utilizar puntos ni puntos suspensivos al final.

      1. Ejemplo commit: `remove a random notification` 
      2. Ejemplo commit: `add a new search feature`
      3. Ejemplo commit: `change the default system color`
      4. Ejemplo commit: `fix a problem with the topbar`
<br>

 Fuente: [Sitio web oficial](https://git-scm.com/docs)
<br>
