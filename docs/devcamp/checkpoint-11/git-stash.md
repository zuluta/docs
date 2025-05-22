---
hide:
  #- navigation
  #- toc
---

## **GIT stash**

El ==git stash== es un comando que se utiliza cuando necesitemos guardar cambios temporalmente en la rama donde estamos trabajando para movernos a cualquier otra rama a realizar cambios de forma rápida.

### **Vamos a simular un ejemplo real**:

Lo primero que debo hacer es, una bifurcación en la rama `main` que se llame `rama-nueva`.

  1. Ejecutamos el comando ==git branch nueva-rama== para crear una nueva rama de trabajo partiendo de `main`.
  2. Ejecutamos el comando ==git switch nueva-rama== para posicionar en la rama que quiero trabajar.
  2. Mientras trabajo en la nueva rama, me piden que debo hacer un cambio rapido en la rama principal `main`.
  3. Si no comiteamos los cambios en la `nueva-rama` antes de ir a `main`, lo que va suceder es que vamos a llevar esos cambios sin comitear a la rama `main`. Cosa que no queremos hacer, ni es el flujo de trabajo correcto llevar esos cambios a la rama `main`. Esto crearia confusión y lo que qeremos es tenerlos por separado.
  4. El problema radica en que recien empezamos a trabajar en la rama `nueva-rama` y no es momento correcto de comitear los cambios todavia. Cada vez que enviamos un `commit`, estamos creando una referencia en el tiempo que prodrías querer revertir en el futuro y todavia no tenemos listo esa versión. Aquí es donde (==git stash==) entra en acción.
  5. Suponiendo que seguimos posicionados en la rama `nueva-rama`, sigamos el siguiente paso.
  6. Ejecutamos el comando ==git stash== para guardar los cambios temporalmente sin agregar archivos al historial ni comitear.
  7. Ejecutamos el comando ==git switch main== para posicionar en la rama `main` y hacer los cambios solicitados.
  8. Cuando aya terminado los cambios en `main`, puedo volver de nuevo a `nueva-rama` y traer los cambios temporales que habia guardado. Para ello,
  9. Ejecutamos el comando ==git stash list== para mostrar el cambio guardado temporalmente (WIP significa trabajo en proceso).
  10. Ejecutamos el comando ==git stash show== para mostrar cuales fueron los cambios del código.
  11. Ejecutamos el comando ==git stash apply== para traer los cambios guardados temporalmente de vuelta.

**Importante:**

Una vez hayamos traido los cambios temporales de vuelta, seguira estando en temporales por lo que hay que borrar ese elemento oculto porque nos puede generar confusión y problemas en el futuro. Para ello, siga el siguiente paso.

**Borrar cambios temporales guardados:**

  1. Ejecutamos el comando ==git stash clear== para borrar todos los cambios temporales guardados.
  2. Ejecutamos el comando ==git stash list== para verificar que no quedo ningun cambio temporal guardado.

**Así se muestra una lista stash:**

```
stash@{0}: RAMA-STASHED-CAMBIOS-SON-PARA: MESSAGE
```

***

## **Comandos stash básicos:**

  - ==git stash== Guarda los cambios de la rama actual en el `stash`.
  - ==git stash save "mensaje"== Guarda los cambios de la rama actual en el `stash` con un mensaje.
  - ==git stash drop== Elimina el último `stash`.
  - ==git stash clear== Elimina todos los cambios temporales guardados en `stash`.
  - ==git stash list== Muesta todos los cambios temporales guardados en el `stash`.
  - ==git stash show== Muetra un resumen de los cambios realizados en el código.
  - ==git stash apply== Aplica los cambios en la rama actual y deja una copia en el `stash`.
  - ==git stash apply stash@{n}== Aplica el `stash` mediante su número dentro de las llaves y deja una copia en el `stash`.
  - ==git stash pop stash@{num_stash}== Aplicar los cambios de un `stash` específico y elimina del `stash`.
  - ==git stash apply NOMBRE-DEL-STASH== Aplica los cambios y deja una copia en el `stash`.
  - ==git stash pop NOMBRE-DEL-STASH== Aplica los cambio y elimina los archivos del `stash`.
  - ==git stash drop NOMBRE-DEL-STASH== Elimina los cambios guardados en `stash` sin aplicarlos.

***

<br>
