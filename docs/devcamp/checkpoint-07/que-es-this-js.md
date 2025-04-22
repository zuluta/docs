---
hide:
  #- navigation
  #- toc
---

# 7. ¿Qué es la palabra clave "this" en JS?
Una de las características de JavaScript que más confusión genera es la palabra clave ==**this**==. Más concretamente a qué o quién hace referencia y en qué circunstancias.

==**this**== es una palabra clave que ==se utiliza mucho dentro de las **clases**== para **hacer referencia al objeto instanciado**. Cuando se crea una función dentro de una clase, esta función  pasa a llamarse **método**. El **primer método siempre sera el constructor**, se encarga de **declarar atributos**, el ==**this**== hace referencia a cualquier atributo que se le pase **dentro de esa misma clase**. si se utilizara fuera de ésta clase, aría referencia a otra cosa.

**Veamos un ejemplo de clase:**

```js title="ejemplo.js"
class Cliente {
    
    provincia = 'Guipuzcoa'; // atributo global / variable de clase

    constructor(nombre, apellido, telefono) {
        this.nombre = nombre;
        this.apellido = apellido;
        this.telefono = telefono;
    }
  
    datos() {
        return 'Nombre: ' + this.nombre + '\n' +
               'Apellido: ' + this.apellido + '\n' +
               'Teléfono: ' + this.telefono + '\n' +
               'Provincia: ' + this.provincia;
    }
}

const cli_1 = new Cliente('Nerea', 'Zelaieta', '666-666-666');
const cli_2 = new Cliente('Roberto', 'Mendiburu', '333-666-666');

console.log(cli_1.datos());
console.log(cli_2.datos());

/*
Salida: Nombre: Nerea
        Apellido: Zelaieta
        Teléfono: 666-666-666
        Provincia: Guipuzcoa
        Nombre: Roberto
        Apellido: Mendiburu
        Teléfono: 333-666-666
        Provincia: Guipuzcoa
*/
```
<br>

**Veamos un ejemplo de objeto:**

```js title="ejemplo.js"
const usuario = {
    nombre: 'Roberto',
    apellido: 'Mendiburu',
    telefono: '333-666-666',

    mostrar() {
        console.log(this);
    }
};

usuario.mostrar();

/*
Salida: Nombre: Roberto
        Apellido: Mendiburu
        Teléfono: 333-666-666
        mostrar: [Function: mostrar]
*/
```

==Cuando se crea una función dentro de un **objeto**==, esta función  pasa a llamarse **método**. ==El **this** hace referencia al **objeto** que lo envuelve==. La ejecución de este código nos ==imprime el objeto completo que el **this** hace referencia==.
<br>
<br>

**Veamos un ejemplo simple:**

```js title="ejemplo.js"
function usuario() {
    console.log(this);
}

console.log(usuario()); // Object [global]

/*
Salida: Object [global]
*/
```

!!! info ""
    Hace referencia al objeto global.
<br>
<br>
