---
hide:
  #- navigation
  #- toc
---

## **Requisitos del Proyecto:**

El documento HTML ya esta construido, no tienes que tocarlo.

El proyecto se debe completar usando solo JavaScript puro. La idea es, que cuando se clique en una de las tareas de la lista de tareas pendientes, este se elimine y pase a la lista de tareas completadas.

No vale ocultar ni cosas por el estilo, debes eliminarlo por completo del DOM y luego volver a crearlo.

```html linenums="1" title="html"
<!DOCTYPE html>
<html lang='en'>

<head>
  <meta charset='UTF-8'>
  <title></title>

  <style>
    .todoItem:hover {
      cursor: pointer;
    }
  </style>
</head>

<body>
  <div class="todos">
    <h2>Pending Todos</h2>
    <ul>
      <li class="todoItem">Lorem ipsum dolor sit amet, consectetur adipisicing elit. Culpa, animi.</li>
      <li class="todoItem">Numquam dolor quo alias nam vel voluptates magni magnam quisquam.</li>
      <li class="todoItem">Recusandae eaque quisquam facere ab reprehenderit cupiditate magni placeat quis?</li>
      <li class="todoItem">Expedita asperiores nam saepe voluptatem, nostrum aliquid debitis quam recusandae.</li>
      <li class="todoItem">Quaerat velit deserunt reprehenderit, vel placeat impedit accusamus non, deleniti!</li>
    </ul>
  </div>

  <h2>Completed Todos</h2>
  <ul class="completedTodoWrapper">
    <div class="completed"></div>
  </ul>
</body>

<script></script>

</html>
```

### Solución:

```js linenums="1" title="javascript"
const todos = document.querySelectorAll('.todoItem');
const completedTodos = document.querySelector('.completed');
const completedTodoWrapper = document.querySelector('.completedTodoWrapper');

todos.forEach(todo => todo.addEventListener('click', (event) => {
    let completedTodo = document.createElement('li');
    let todoContent = document.createTextNode(todo.textContent);
    completedTodo.appendChild(todoContent);
    completedTodoWrapper.insertBefore(completedTodo, completedTodos);
    todo.remove();
}))
```

***

<br>
