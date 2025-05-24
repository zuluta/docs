---
hide:
  #- navigation
  #- toc
---

## **Como retroceder un archivo a un commit específico**

Retroceder un archivo en el tiempo a un punto en la que estaba funcionando bien, es una tarea bastante frecuente y vamos a ver como hacerlo.

Lo primero que debemos hacer es, revisar el histórico completo de GIT, para conocer a que estado queremos retroceder.

  - ==git log== para mostrar el histórico de commits.
  - ==git log --oneline== para mostrar información simplificada de commits donde sale el hash de cada uno.

>Nota: El (==git log --oneline==) nos muestra los primeros 7 caracteres del hash.

**Para navegar en el histórico de GIT:**

  - Tecla (j) para bajar.
  - Tecla (k) para subir.
  - Tecla (q) para salir.
  - Tecla (Shift + g) para ir hasta el final.

Cuando tengamos claro a que estado queremos retroceder, copia la (hash) de ese commit y salimos del histórico.

  - ==git checkout f91c94d -- ruta-archivo/archivo.js== para retroceder archivo al commit mediante hash (f91c94d), no elimina commits.
  - ==git status== para mostrar el estado de los procesos GIT, ahora si tenemos cambios sin confirmar.

>Nota: Lo bueno de esto, es que nos deja los cambios sin confirmar y lo podemos comitear nosotros mismos como queramos.

  - ==git add .== para añadir todos los archivos al GIT.
  - ==git commit -m "Retroceder el archivo.js al hash f91c94d"== para añadir un commit al GIT.

Si todo esta correcto, actualizamos nuestro repositorio remoto con este nuevo cambio.

  - ==git push origin main== Sube los archivos a la rama (main) remoto de GitHub.

***

## **Investigar código específico del pasado de una rama**

Esta técnica, se utiliza principalmente para investigar el código de una rama en el tiempo de un commit especifico. Lo que hace es crear una nueva rama en el punto donde se creo ese commit mediante un hash.

  - ==git checkout f91c94d -b investigacion==

El código anterior, crea una nueva rama (investigacion) y a la vez te posiciona en ella. Esto revierte en una nueva rama todos los archivos al estado que se encontraban en ese commit sin alterar la rama original. Se utiliza especialmente cuando queremos invertigar en profundidad en que momento fallo nuestra aplicación sin perder el código actual y trabajar en paralelo con las 2 ramas hasta que podamos solucionar.

A partir de aqui, cuando ya localicemos los errores y en que commit funcionaban bien, podemos revertir esos archivos a esos commit en la rama original. Esto nos permite revertir a un estado especifico de forma segura una vez investigado.

Para finalizar, solo queda eliminar la rama (investigacion), ya no la necesitamos.

  - ==git branch -d investigacion== para eliminar la rama (investigacion) del repositorio local.
  - ==git branch== para mostrar todas las ramas locales y distingue con un (*) la rama actual.

De este modo, hemos logrado localizar un estado funcional de la aplicación en commits anteriores, comprobar en una nueva rama (investigacion) y seleccionar los archivos a recuperar.

A continuación, procedemos a recuperar cada uno de esos archivos seleccionados.

  - ==git checkout f91c94d ruta-archivo/archivo.js== para retroceder archivo al commit mediante hash (f91c94d), no elimina commits.

Una vez recuperados todos los archivos, procedemos a confirmar los cambios.

  - ==git add .== para añadir todos los archivos al GIT.
  - ==git commit -m "Retroceder el archivo.js al hash f91c94d"== para añadir un commit al GIT.

Si todo esta correcto, actualizamos nuestro repositorio remoto con este nuevo cambio.

  - ==git push origin main== Sube los archivos a la rama (main) remoto de GitHub.

***

## **Como resetear un proyecto completo a un commit específico**

Todo lo que hemos aprendido hasta ahora, es necesario conocer bien para trabajar en el dia dia y no cometer errores.

Para resetear un proyecto en el tiempo a un commit específico, hay que tener muchísimo cuidado, no es algo que vayas hacer a menudo porque estarias eliminando todos los commits hacia atras hasta llegar al commit deseado. Una vez eliminado todo ese pedazo, queda eliminado y no hay vuelta atras. Si miramos en el histórico de commits, veremos que todos esos commits fueron elimnados y no apareceran.

Todo esto se vuelve todavia mas peligroso cuando estemos trabajando en un equipo ya que podriamos ocasionar todo tipo de conflictos.

Cuando vayas a realizar un retroceso de este calibre, seria mas inteligente optar por el procedimiento anterior donde se aisla una rama (investigacion) y recuperas solo los archivos seleccionados, de esta forma evitaremos alterar todo el histórico.

Recordar que este proceso puede eliminar un gran número de commits dependiendo hasta donde queremos retroceder en el tiempo.

Primero de todo, es investigar a que commit queremos retroceder.

  - ==git checkout f91c94d -b investigacion==

>Nota: El nombre de la rama puede ser cualquiera, en este caso, se utiliza (investigacion) simplemente para diferenciar que se trata de una rama para investigar nada mas.

Si accedemos al código del archivo que necesitemos analizar, podemos ver las diferencias respecto a la rama (main) actual.

  ==git switch main==

De esta forma, podemos ir analizando manualmente las diferencias que hay en el código entre las 2 ramas.

Una vez analizado y llegado el momento, decidimos retroceder todo el proyecto a un commit específico.

  - ==git reset --hard f91c94d==

Si ejecutamos el siguiente comando, veremos que efectivamente todos los commits que se encontraban entre el commit retrocedido y el mas reciente, fueron eliminados y retrocedio correctamente.

  - ==git log== para mostrar el histórico de commits.

Si ejecutamos el siguiente comando, veremos que no hay cambios que confirmar pero nos avisa de que estamos por ejemplo 20 commits por detras sobre la rama (main) remoto.

Para actualizar la rama (main) remoto, debemos forzar (-f) la subida.

  - ==git push -f origin main== para forzar la subida de los archivos a la rama (main) remoto de GitHub

Entra en GitHub y verifica el código de los archivos.

>Nota: (git push -u origin main) con el comando opcional (-u) primero obtiene las actualizaciones remotas antes de lanzar la subida. En nuestro caso, lo que queremos es directamente forzar (-f) la subida sin obtener las actualizaciones remotas.

***

## **Comandos básicos:**

  - ==git log== Muestra el histórico de commits.
  - ==git log --oneline== Muestra información simplificada de commits donde sale el hash de cada uno.
  - ==git status== Muestra el estado de los procesos GIT.
  - ==git branch== Muestra todas las ramas locales y distingue con un (*) la rama actual.
  - ==git checkout -b investigacion== Crea una nueva rama (investigacion) a partir de la rama actual y te posiciona en ella.
  - ==git branch -d investigacion== Elimina la rama (investigacion) del repositorio local.
  - ==git switch main== Cambia de la rama actual a la rama (main).
  - ==git checkout f91c94d -- ruta-archivo/archivo.js== Retrocede archivo al commit mediante hash (f91c94d), no elimina commits.
  - ==git reset 20cf9cb== Regresa al commit mediante hash (20cf9cb) y elimina todos los commits posteriores a este.
  - ==git reset --hard 20cf9cb== Regresa al commit mediante hash (20cf9cb), elimina todos los commits posteriores a este y sobrescribe todos los cambios en el directorio de trabajo.
  - ==git add .== Añade todos los archivos al GIT.
  - ==git commit -m "Retroceder el archivo.js al hash f91c94d"== Añade un commit al GIT.
  - ==git push origin main== Sube los archivos a la rama (main) remoto de GitHub.
  - ==git push -f origin main== Fuerza la subida de los archivos a la rama (main) remoto de GitHub.
 
 ***

 <br>
