# <center>Gestor de documentos</center>

![Git Hub Image](images/index/portada.png)
<br>

## Commands

* `mkdocs new [dir-name]` - Create a new project.
* `mkdocs serve` - Start the live-reloading docs server.
* `mkdocs build` - Build the documentation site.
* `mkdocs -h` - Print help message and exit.

## mkdocs.yml config

```
# project information
site_name: zuluta.dev
site_url: https://zuluta.github.io

site_author: zuluta
site_description: mkdocs

#extra:
  #homepage: https://zuluta.github.io

# repository
repo_name: zuluta
repo_url: https://github.com/zuluta

# navigation
nav:
  - Inicio: index.md
  - 💻 Manuales de Instalación:
    - MkDocs + virtualenv: mkdocs.md
  - 📚 Documentación:
    - Checkpoint 06: doc_06.md
    - Checkpoint 07: doc_07.md

# configuration
theme:
  name: material
  language: es

  font:
    text: Roboto
    code: Roboto Mono

  features:
    #- navigation.tabs
    - navigation.sections
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

  # extension para crear note, abstract, info, tip, success, question, warning, failure, danger, bug, example, quote
  - admonition
  - pymdownx.details
  - pymdownx.superfences

copyright:
  Copyright &copy; 2025 <a href="https://github.com/zuluta"  target="_blank" rel="noopener">zuluta</a>
```
