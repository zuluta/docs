---
hide:
  #- navigation
  - toc
---

# 2. ¿Qué es un método dunder?

<p>En programación orientada a objetos, los métodos dunder o métodos mágicos son funciones especiales que permiten definir comportamientos específicos para las clases. Estos métodos se llaman “mágicos” porque su nombre comienza y termina con dos guiones bajos (__).</p>

!!! tip "TIP"
    Los métodos mágicos son una herramienta poderosa que permite definir comportamientos específicos para las clases en Python. Utilizarlos de forma adecuada puede hacer que nuestro código sea más fácil de entender y mantener.
<br>

### 2.1. Tipos de métodos dunder:

- `__init__`: Se utiliza para inicializar objetos y es invocado automáticamente cuando se crea una instancia de la clase.
- `__str__`: Se utiliza para representar el objeto en forma de cadena de texto.
- `__len__`: Permite determinar la longitud de un objeto.

<p>Existen muchos otros métodos mágicos que pueden ser útiles, como <code>__add__</code> (para sumar objetos), <code>__eq__</code> (para comparar igualdad), <code>__lt__</code> (para comparar menor que), entre otros. Sin embargo, es importante tener en cuenta que no siempre es necesario utilizar estos métodos y que su uso variará dependiendo de cada caso específico.</p>
<br>

- Ejemplo `__init__`:
```python
class Persona:
    def __init__(self, nombre):
        self.nombre = nombre

p = Persona('Juan')
print(p.nombre)
```

- Ejemplo `__init__` con `__str_`:
```python
class Persona:
    def __init__(self, nombre):
        self.nombre = nombre

    def __str__(self):
        return f'Mi nombre es {self.nombre}'

p = Persona('Juan')
print(p)
```

- Ejemplo `__init__` con `__len__`:
```python
class Lista:
    def __init__(self, elementos):
        self.elementos = elementos

    def __len__(self):
        return len(self.elementos)

l = Lista([1,2,3,4,5])
print(len(l)) # Imprime 5
```

!!! info "IMPORTANTE"
    El primer ejemplo y el segundo ejemplo tienen el mismo resultado, lo que hace el método dunder `__str__` es convertir el objeto en una cadena de texto.
<br>

###  2.2. ¿Qué método dunder se ejecuta automáticamente?

<p>El método <code>__init__</code>, es un método especial que se <strong>ejecuta automáticamente</strong> al invocar la clase e inicializara los atributos del objeto que le ayamos creado. Es decir, es imposible de olvidarse llamarlo ya que se llamará automáticamente.</p>

!!! info "IMPORTANTE"
    El método `__init__` es el primer método que se ejecuta dentro de una clase.
<br>

### 📝 Características:

- El método `__init__` no puede retornar <code>return</code> datos, no devuelve nada.
- El método `__init__` puede recibir parámetros que se utilizan para inicializar atributos de forma automática.
- El método `__init__` es un constructor de instancias.
- El método `__init__` es un método opcional, de todos modos es muy común declararlo.
<br>
<br>
