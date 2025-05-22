---
hide:
  #- navigation
  #- toc
---

## **GIT merge**

En GIT, (==git merge==) es un comando que se utiliza para fusionar los cambios de una rama en otra. Es decir, se utiliza para integrar las modificaciones realizadas en una rama de desarrollo (por ejemplo, una rama con una nueva funcionalidad) en la rama principal o en otra rama elegida. Este proceso de integración se hace manteniendo el historial completo de versiones, unificando los `commits` de ambas ramas.

**Arbol inicial:**

1. Ejecuto el comando ==git branch rama-test== para crear una nueva rama de trabajo (**puede ser compartido**).
2. Mientras yo trabajo en la rama `rama-test`, otra persona realiza 4 cambios (I, J, K, L) en la rama principal `main`.

```
       /A----B----C---D rama-test
--F-G--H--I---J---K---L main
```

  1. Lo primero que debo hacer es traer todos los cambios de la rama `main` a mi ordenador.
  2. Ejecuto el comando ==git branch== para ver todas mis ramas locales y me muestre en cual estoy posicinado.
  3. Ejecuto el comando ==git switch main== para posicionar en la rama que quiero actualizar.
  4. Ejecuto el comando ==git pull== para traer todos los cambios a la rama actual.
  5. Ejecuto el comando ==git merge rama-test== para fusionar la rama `rama-test` a la rama actual con todos sus cambios.

La fusión se hace del punto (D) de la rama `rama-test` al nuevo punto (M) de la rama principal `main`.

**Arbol despues del `merge`:**

```
       /A----B----C----D\ rama-test
--F-G--H--I---J---K---L-M--- main
```

>Nota: ==git merge== no elimina automáticamente la rama que se está fusionando. Tras una fusión, ambas ramas siguen existiendo en el repositorio, y la rama que fue fusionada puede ser eliminada si se considera que ya no es necesaria.

***

## **GIT rebase**

Realizar un rebase a una rama `branch` en GIT es una forma de desplazar la totalidad de la rama a otro punto del árbol. El ejemplo más simple es desplazar la rama de mas arriba en el árbol.

Digamos que tenemos la rama `branch` que se separó de la rama `main` en el punto `A`:

```
        /o-----o---o--o-----o--------- branch
--o-o--A--o---o---o---o----o--o-o-o--- main
```

Cuando se realiza `rebase` se puede desplazar la rama así:

```
                                   /o-----o---o--o-----o------ branch
--o-o--A--o---o---o---o----o--o-o-o main
```

Para realizar `rebase`, asegúrate de tener todos los `commits` que quieras en el `rebase` en tu rama `main`. Una vez revisado la rama en la que quieres hacer el `rebase`, ejecuta el comando (==git rebase main==) (donde `main` es la rama en la que quieres hacer el `rebase`).

También es posible hacer `rebase` en una rama diferente, de modo que, por ejemplo, una rama que se basaba en otra rama (llamémosla `feature`) se rebasa en `main`:

```
                            /---o-o branch
           /---o-o-o-o---o--o------ feature
----o--o-o-A----o---o--o-o-o--o--o- main
```

Después de (==git rebase main branch==) o si te encuentras en la rama `branch` (==git rebase main==) obtendrás:

```
           /---o-o-o-o---o--o------ feature
----o--o-o-A----o---o--o-o-o--o--o- main
                                  \---o-o branch
```

>Importante: Nunca hagas `rebase` en ramas bifurcadas y compartidas con otras personas porque causara todo tipo de conflictos cuando la otra persona intente ejecuta cualquier otro comando git en la misma rama. Aparte de arruinar su trabajo, podria ser la causa de un despido, procura no cometer ese error.

### **Flujo de trabajo correcto con rebase:**

**Arbol inicial:**

  1. Ejecuto el comando ==git branch rama-test== para crear mi propia rama de trabajo (**no es compartido**).
  2. Mientras yo trabajo en mi rama `rama-test`, otra persona realiza 4 cambios (I, J, K, L) en la rama principal `main`.

```
       /A---B---C---D--- rama-test
--F-G--H--I---J---K----L main
```

  1. Lo primero que debo hacer es traer todos los cambios de la rama `main` a mi ordenador.
  2. Ejecuto el comando ==git branch== para ver todas mis ramas locales y me muestre en cual estoy posicinado.
  3. Ejecuto el comando ==git switch main== para posicionar en la rama que quiero actualizar.
  4. Ejecuto el comando ==git pull== para traer todos los cambios a la rama actual.
  5. Ejecuto el comando ==git switch rama-test== para posicionar en la rama `rama-test`.
  6. Ejecuto el comando ==git rebase main== para desplazar mi rama bifurcada del punto (H) al punto (L).

**Arbol despues del `rebase`:**

```
                        /A---B---C---D--- rama-test
--F-G--H--I---J---K-----L main
```

De este modo, obtengo todos los cambios que a realizado la otra persona en la rama principal `main` y sigo trabajando en mi propia rama `rama-test`.

Ahora que ya termine de trabajar en la rama `rama-test`, decido fusionar `rama-test` en la rama principal `main`.

  1. Ejecuto el comando ==git branch== para ver todas mis ramas locales y me muestra en cual estoy posicinado.
  2. Ejecuto el comando ==git switch main== para moverme a la rama donde quiero fusionar.
  3. Ejecuto el comando ==git merge rama-test== para fusionar la rama `rama-test` a la rama actual con todos sus cambios.

>Nota: ==git merge== no elimina automáticamente la rama que se está fusionando. Tras una fusión, ambas ramas siguen existiendo en el repositorio, y la rama que fue fusionada puede ser eliminada si se considera que ya no es necesaria.

***

<br>
