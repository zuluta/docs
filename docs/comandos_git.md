---
hide:
  #- navigation
  - toc
---

# GIT desde la línea de comandos

### Comandos básicos para trabajar en localhost:

  - `git init` Iniciar GIT
  - `git add .` Agrega todos los archivos al GIT
  - `git commit -m 'primer commit'` Agrega un commit

### Comandos para sincrinizar por primera vez GIT con GitHub desde terminal de VSCode:

  - `git init` Iniciar GIT
  - `git config --global user.name "Your_Name"` Usuario de GitHub
  - `git config --global user.email "you@example.com"` Email de GitHub

### Comandos basicos para subir nuestro proyecto localhost al repositorio de GitHub:

  - `git init` Iniciar GIT
  - `git add .` Agrega todos los archivos al GIT
  - `git commit -m 'primer commit'` Agrega un commit
  - `git branch -M main` Cambia a la rama main
  - `git remote add origin https://github.com/usuario/mi_repositorio.git` Asigna url del repositorio GitHub
  - `git remote -v` Verifica la comunicación con el repositorio remoto
  - `git status` Muestra el estado de los procesos GIT
  - `git push -u origin main` Sube los archivos a la rama main de GitHub

### Comandos útiles:

  - `git status` Muestra el estado de los procesos GIT
  - `git add ejemplo.html` Agrega los archivos indibidualmente al GIT
  - `git branch -M main` Cambia a la rama main
  - `git remote -v` Verifica la comunicación con el repositorio remoto
  - `git log` Muestra el histórico de commits
  - `git log -n 2` Muestra los últimos 2 commits
  - `git log prueba.html` Muestra los commits del archivo (prueba.html)
  - `git commit --amend` Edita el mensajes del commit

### Comandos para restaurar el archivo a un commit específico:

  - `git log --oneline` Muestra información simplificada de commits
  - `git restore --source 20cf9cb prueba.html` Restaura el archivo (prueba.html) al commit referenciado con un hash
<br>
<br>
