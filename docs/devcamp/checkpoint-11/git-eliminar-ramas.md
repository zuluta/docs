---
hide:
  #- navigation
  #- toc
---

## **GIT como eliminar una rama local**

Es de buena práctica, eliminar una rama que ya a sido fusionado a la rama principal. La razón de eliminar es que podemos evitar conflictos en el futuro en caso de que entremos a esa rama por error y realicemos cambios. Si estamos trabajando en un proyecto grande, lo mas seguro es que tengamos bastantes ramas y esa es la razón de ir eliminando las ramas ya terminadas y fusionadas al `main`.

Suponiendo que ya tenermos una rama `nueva-rama` ya terminada y fusionada a la rama principal `main`, procedemos a eliminarla.

  - Ejecutamos el comando ==git switch main== para posicionar en la rama principal `main`.
  - Ejecutamos el comando ==git branch -d nueva-rama== para eliminar la rama `nueva-rama` ya fusionada.
  - Ejecutamos el comando ==git branch== para mostrar todas las ramas y verificar si la a eliminado.


## **Git como eliminar una rama remota**

Para eliminar una rama remota de GitHub, seguimos el sigiente paso.

  - Ejecutamos el comando ==git push origin --delete nueva-rama== para eliminar la rama `nueva-rama` remoto.
  - Entra en GitHub para verificar si la a eliminado o desde la termina con el siguiente paso.
  - Ejecutamos el comando ==git branch -r== para mostrar todas las ramas del repositorio remoto.

***

## **Comandos básicos:**

  - ==git branch -d nueva-rama== Elimina la rama (nueva-rama) del repositorio local si esta fusionado con (main).
  - ==git branch -D nueva-rama== Fuerza a eliminar la rama (nueva-rama) del repositorio local este o no fusionado con (main).
  - ==git push origin --delete nueva-rama== Elimina la rama (nueva-rama) del repositorio remoto.
  - ==git branch== Muestra todas las ramas locales y distingue con un (*) la rama actual
  - ==git branch -a== Muestra todas las ramas, tanto locales como remotas y distingue con un (*) la rama actual.
  - ==git branch -r== Muestra todas las ramas del repositorio remoto.

***

<br>
