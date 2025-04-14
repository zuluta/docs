---
hide:
  #- navigation
  - toc
---

# Mi configuración de MkDocs v1.6.1

## Commands

* `mkdocs new [dir-name]` - Create a new project.
* `mkdocs serve` - Start the live-reloading docs server.
* `mkdocs build` - Build the documentation site.
* `mkdocs -h` - Print help message and exit.

## mkdocs.yml config

```
# project information
site_name: zuluta.dev
site_url: https://zuluta.github.io/docs/

site_author: zuluta
site_description: mkdocs

extra:
  homepage: https://zuluta.github.io/docs/

# repository
repo_name: docs
repo_url: https://github.com/zuluta/docs/

# navigation
nav:
  - Manual de programación:
      - Introducción: index.md
      - Ruta de aprendizaje:
          - Desarrollador Full Stack: ruta_aprendizaje/desarrollador_full_stack.md
      - Programación:
          - Comandos GIT: programacion/comandos_git.md
      - Instalación:
          - MkDocs + virtualenv: instalacion/mkdocs.md
          - Despliegue a GitHub Pages: instalacion/gh_deploy.md
      - DevCamp documentación:
          - Checkpoint 06: devcamp/checkpoint-06/checkpoint_06.md
          - Checkpoint 07:
              - Índice: devcamp/checkpoint-07/indice.md
              - 1. ¿Que diferencia a JavaScript de cualquier otro lenguaje de programación?: devcamp/checkpoint-07/introducción-js.md
              - 2. ¿Cuáles son algunos tipos de datos JS?: devcamp/checkpoint-07/tipos-de-datos-js.md
              - 3. ¿Cuáles son las tres funciones de String en JS?: devcamp/checkpoint-07/tres-funciones-de-string-js.md
              - 4. ¿Qué es un condicional?: devcamp/checkpoint-07/condicionales-js.md
              - 5. ¿Qué es un operador ternario?: devcamp/checkpoint-07/operador-ternario-js.md
              - 6. ¿Cuál es la diferencia entre una declaración de función y una expresión de función?: devcamp/checkpoint-07/declaracion-de-funcion-vs-expresion-de-funcion-js.md
              - 7. ¿Qué es la palabra clave "this" en JS?: devcamp/checkpoint-07/que-es-this-js.md
          - Checkpoint 08:
              - Índice: devcamp/checkpoint-08/indice.md

# configuration
theme:
  name: material
  language: es
  #favicon: images/favicon.png
  icon:
    logo: fontawesome/solid/hat-cowboy

  font:
    text: Roboto
    code: Roboto Mono

  features:
    - navigation.tabs
    #- navigation.sections
    #- toc.integrate
    #- navigation.expand
    - navigation.top
    - search.suggest
    - search.highlight
    #- content.tabs.link
    #- content.code.annotation
    - content.code.copy
    #- header.autohide

  palette:
    # light mode
    - scheme: default
      primary: teal
      accent: deep orange
      toggle:
        icon: material/weather-sunny
        name: Light Mode

    # dark mode
    - scheme: slate
      primary: teal
      accent: deep orange
      toggle:
        icon: material/weather-night
        name: Dark Mode

markdown_extensions:
  # extension para sintaxis de codigo
  - pymdownx.highlight:
      anchor_linenums: true
  - pymdownx.superfences

  # extension para emojis
  - attr_list
  - pymdownx.emoji:
      emoji_index: !!python/name:material.extensions.emoji.twemoji
      emoji_generator: !!python/name:material.extensions.emoji.to_svg

  # extension para crear note, abstract, info, tip, success, question, warning, failure, danger, bug, example, quote
  - admonition
  - pymdownx.details
  - pymdownx.superfences

  # extension para el resaltado de texto
  - pymdownx.critic
  - pymdownx.caret
  - pymdownx.keys
  - pymdownx.mark
  - pymdownx.tilde

copyright:
  Copyright &copy; 2025 <a href="https://github.com/zuluta"  target="_blank" rel="noopener">zuluta</a>
```
<br>
