---
hide:
  #- navigation
  #- toc
---

## **GIT gestionar conflictos de fusión**

Un conflicto de fusión es, cuando tu o un miembro del equipo realiza cambios en un mismo archivo y en la mayoria de las veces, en las mismas líneas de código. Para muchos programadores, es un verdadero quebradero de cabeza solucionar conflictos y más, cuando el conflicto se genera en múltiples archivos.

Para ello, crearemos un simple conflicto de fusión.

  - Un compañero realiza cambios de código en 2 archivos de la rama (main) en GitHub.
  - Yo desde mi repositorio local, me posiciono en la rama (main) y realizo los mismos cambios en los 2 archivos.

Mientras yo trabajo en local, desconozco lo que otros compañeros estan realizando en este mismo repositorio remoto.

  - ==git status== para verificar que existen 2 archivos modificados en local.
  - ==git add .== para añadir todos los archivos al GIT.
  - ==git commit -m "2 archivos actualizados"== para añadir un commit al GIT.

De momento, todo parece estar bien pero, en realidad, tenemos un problema porque hemos hecho cambios a la mismas líneas de código que nuestro compañero tambien modificó.

Se ha creado un conflicto pero todabia no lo sabemos.

  - ==git fetch origin== para descarga nuevos cambios desde un repositorio remoto a la rama actual del repositorio local.
  - ==git status== para mostrar el estado de los procesos GIT.

Mediante un mensaje, nos avisa que en nuestra rama y en la rama remota existen 1 o 2 commits diferentes en cada una.
Aquí radica la diferencia entre `git fetch` y `git pull`. En este caso, nos faltaria el segundo paso que es la de fusionar.
Si de primeras, hubiésemos ejecutado un `git pull` para automatizar, no se llegarian a descargar los cambios del remoto al local para verificar el código y reparar el conflicto ya que la ejecución resultaria fallida.

>Importante: Cuando se trabaja en equipo en un mismo repositorio, se recomienda utilizar `git fetch` para traer nuevos cambios del remoto al local, este comando, nos da la posibilidad de verificar algun tipo de mensaje que nos pueda mostrar antes de fusionar a otra rama porque trabajar en equipo, pueden surgir conflictos.

  - ==git merge origin main== para fusionar los cambios a nuestra rama (main) local.

Nos avisa en que archivos se estan generando los conflictos y que la fusión automática a fallado. Primero debemos arreglar el conflicto y luego fusionar.

  - ==git status== para obtener mas información del conflicto.

Nos dice que ambos archivos han sido modificados, refiriendose al archivo local y remoto. Ese seria el problema que nos esta generando el conflicto.

Para solucionar el conflicto, debemos elegir si quedarnos con los cambios del remoto o las nuestras del local. Para ello, abrimos el archivo que esta generando el conflito y buscamos las líneas que coinciden los cambios locales y remotos. Veremos algo parecido a lo que muestro a continuación.

```
<<<<<< HEAD
linea de codigo modificado en repositorio local
======
linea de codigo modificado en repositorio remoto
>>>>>> origin main
```

Nos da la opción de quedarnos con una de las 2 ocpciones, bien con nuestro cambio local o el cambio remoto. En este punto, podemos conversar con nuestro compañero que añadio ese cambio y decidir entre los 2 con cual de los 2 códigos qedarnos.

Una vez decididos en quedarnos con los cambios del compañero, debemos eliminar nuestra línea de código y los caracteres que lo envuelven.

>Nota: Esos caracteres nos ayudan a identificar la línea del código en conflicto.

```
linea de codigo modificado en repositorio remoto
```

Una vez eliminado el cambio descartado, nuestro conflicto quedara resuelto y podemos guardar el archivo.

>Nota: En caso de tener conflictos en mas archivos, seguir el mismo procedimiento.

Una vez resuelto todos los conflictos, procedemos.

  - ==git add .== para añadir todos los archivos al GIT.
  - ==git commit -m "2 archivos actualizados"== para añadir un commit al GIT.
  - ==git push origin main== para subir los archivos a la rama (main) remoto de GitHub.

Entra en GitHub y verificar el archivo resuelto del conflicto.

>Nota: Los conflictos de fusión no son una cosa mala, son molestos en resolver, pero es GIT haciendo su trabajo donde te da la posibilidad de escoger entre guardar o desechar.

***

### **Cancelar una operación de fusión**:

==git merge --abort== es un comando de GIT que se utiliza para cancelar o abortar una fusión en curso. Esta operación deshace la fusión, restaurando el directorio de trabajo y el índice al estado anterior al inicio del proceso de fusión. Es como si nunca hubieras intentado fusionar las ramas.

***

## **Comandos básicos:**

  - ==git fetch origin== Descarga nuevos cambios desde un repositorio remoto a la rama actual del repositorio local.
  - ==git status== Muestra el estado de los procesos GIT.
  - ==git merge origin main== Fusiona la rama remota (main) a la rama actual del repositorio local.
  - ==git merge --abort== Cancela una fusión en curso al estado anterior a la fusión.
  - ==git add .== Añade todos los archivos al GIT.
  - ==git commit -m "2 archivos actualizados"==  Añade un commit al GIT.
  - ==git push origin main== Sube los archivos a la rama (main) remoto de GitHub.

***

<br>
