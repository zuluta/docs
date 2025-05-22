---
hide:
  #- navigation
  #- toc
---

## **GIT fetch**

### **Volver a sincronizar el repositorio local con el remoto**

Si hemos editado el repositorio de forma remota, es evidente pensar que los cambios no se verán reflejados en el repositorio local. Y así es.

Para volver a sincronizar el repositorio local con el remoto, debemos ejecutar los siguientes comandos:

  - ==git fetch origin==
  - ==git merge origin main==

Esta opción es equivalente a ejecutar el siguiente comando, pero es más recomendable ejecutar los dos comandos anteriores:

  - ==git pull origin main==

***

## **GIT pull**

Si se usa el comando (==git pull==), se ejecutan los comandos (==git fetch==) y (==git merge==) de forma automática, lo que significa que no podemos ver los cambios que se han realizado en el repositorio remoto antes de realizar el `merge`.

***

## **Comandos básicos:**

  - ==git fetch origin== Descarga nuevos cambios desde un repositorio remoto a la rama actual del repositorio local.
  - ==git merge origin main== Fusiona la rama remota (main) a la rama actual del repositorio local.
  - ==git pull origin main== Actualiza la rama actual del repositorio local con los nuevos cambios efectuados en la rama (main) del repositorio remoto.

***

<br>
