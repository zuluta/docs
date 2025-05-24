---
hide:
  #- navigation
  #- toc
---

## **GIT como volver al último commit**

Una de las principales razónes de utilizar GIT es que te vas a sentir seguro programando ya que si cometes un error sabes que vas a poder revertir a cualquier punto anterior comiteado.

Antes de nada, vamos a verificar que no tengamos nada pendiende en el seguimiento del GIT.

  - ==git status== para verificar que no tengamos nada pendiente en el stado de los procesos GIT en la rama actual.

Ahora vamos a borrar algunas líneas de codigo en varios archivos y guardamos los cambios, volvemos a mirar el estado del GIT.

  - ==git status== para mostrar el estado de los procesos GIT, ahora si tenemos cambios sin confirmar.

### **Análisis de diferencias entre estados**:

==git diff== es un comando versátil de Git que te permite ver las diferencias entre diferentes estados de tus archivos, ramas, o confirmaciones (commits) dentro de tu repositorio de código. Es como una lupa que te muestra exactamente qué ha cambiado entre dos puntos en el tiempo.

  - ==git diff archivo.js== para mostrar los cambios efectuados en el código de ese archivo respecto al último commit.

>Los guiones (==-==) significan que esas líneas han sido eliminados en el código actual respecto al último commit.


### **Retroceder al último commit**

Si tenemos cambios sin confirmar, y deseamos borrar todos los cambios y retroceder al último commit, ejecutamos el siguiente comando.

  - ==git checkout .== para borrar todos los cambios y regresar al estado del último commit.
  - ==git status== para mostrar el estado de los procesos GIT, ahora no tenemos cambios para confirmar.

>Hemos retrocedido al estado del último commit.

### **Borrar cambios sin tener commit**

Si tenemos un nuevo archivo sin comitear y ejecutamos el siguiente comando.

  - ==git status== para mostrar el estado de los procesos GIT, ahora si tenemos cambios sin confirmar.

La forma de eliminar esos cambios del GIT es eliminando el archivo ya que no tiene ningun commit todavia.

  - ==del archivo.js== para eliminar el archivo desde la terminal en windows.
  - ==git status== para mostrar el estado de los procesos GIT, ahora no tenemos cambios para confirmar.

>Nota: El comando (==del==) no es de GIT, es un comando exclusivo de windows para eliminar archivos.

***

## **Comandos básicos:**

  - ==git status== Muestra el estado de los procesos GIT.
  - ==git diff archivo.js== Muestra todos los cambios efectuados en el código de ese archivo respecto al último commit.
  - ==git checkout .== Borra todos los cambios y retrocede al estado del último commit.
 
 ***

 <br>
