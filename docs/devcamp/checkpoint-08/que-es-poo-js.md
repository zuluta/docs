---
hide:
  #- navigation
  #- toc
---

La **programación orientada a objetos** (POO) es un paradigma de la programación en el que ==se crean objetos== para la manipulación de datos y donde, por lo general, ==cada objeto ofrece una funcionalidad especial==.

  - La idea básica de la POO es el uso de objetos para modelar cosas del mundo real.
  - POO nos ayuda a la reutilización del código.

Imagina que tienes un colegio o escuela con 1000 estudiantes y 100 profesores, sería ilógico estar construyendo objetos para cada uno de ellos. ==Las clases son, como una especie de máquina constructora de objetos al momento segun demanda==.

**Hay de varios tipos:**

  - ==Función constructora== (antiguo)
  - ==Clase== (actual)
***
<br>

## **6.1. Funciones constructoras:**

  - Un **nombre de función constructora** generalmente ==comienza con una letra mayúscula==. Esta convención se utiliza para hacer que la función constructora sean más ==fácil de reconocer en el código==.
  - La palabra clave **new** se usa para ==crear una nueva instancia del objeto== (crear un nuevo objeto)

### :material-code-braces: ==Declaración de función== + ==1 atributo== + ==instancia==:
```js linenums="1"
function Persona(nombre) {
    this.nombre = nombre;
    this.saludar = function() {
        return (`${this.nombre} dice, ¡hola!`);
    };
}

const persona_1 = new Persona('Markel');
const persona_2 = new Persona('Nerea');

console.log(persona_1.saludar());
console.log(persona_2.saludar());

/* Salida:

Markel dice, ¡hola!
Nerea dice, ¡hola!

*/
```

### :material-code-braces: El constructor ==Object()==:

```js linenums="1"
const persona_1 = new Object();
persona_1.nombre = "Markel";
persona_1.saludar = function() {
    return (`${this.nombre} dice, ¡hola!`);
};

console.log(persona_1.saludar());

/* Salida:

Markel dice, ¡hola!

*/
```
***
<br>

## **6.2. Clases:**
Con la llegada de **ES6** (ECMAScript 2015), ==se introducen las **clases** en JavaScript== que ==proveen una sintaxis mucho más clara y simple para crear objetos== y lidiar con la herencia. ==Es una mejora sintáctica de las **funciones constructoras**== que se basaban en prototipos, ésto no cambió ni agregó funcionalidad, pero trajo una mejor organización del código.

### Existen 2 formas para definir una clase y 2 tipos de expresión de clase:

  - ==Declaración de clase==
  - ==Expresión de clase==
    - **Anónima**: No tiene un nombre.
    - **Nombrada**: Tiene un nombre interno que solo es accesible dentro de la clase.

### :material-arrow-right-box: Declaración de clase:

```js linenums="1"
class Persona {
    constructor(nombre) {
        this.nombre = nombre;
    }
}
```

### :material-arrow-right-box: Expresión de clase:
```js linenums="1"
const Persona = class {
    constructor(nombre) {
        this.nombre = nombre;
    }
};
```
Ambos enfoques crean una **clase** llamada ==Persona==, pero ==con las **expresiones de clases** se tiene más flexibilidad para definirlas de forma dinámica==.

### :material-arrow-right-box: Expresión de clase:
En el siguiente ejemplo, ==la **clase** se define sin un nombre específico== (anónima) y ==se asigna a la **constante** Persona==. A partir de ahí, ==se puede utilizar de la misma manera que una **clase declarada**==.

```js linenums="1"
const Persona = class {
  constructor(nombre, edad) {
    this.nombre = nombre;
    this.edad = edad;
  }

  saludar() {
    console.log(`Hola, soy ${this.nombre} y tengo ${this.edad} años.`);
  }
};

const persona_1 = new Persona('Roberto', 34);

persona_1.saludar(); // Hola, soy Roberto y tengo 34 años.
```

### :material-arrow-right-box: Expresión de clase nombrada:
En este ejemplo, la **clase** ==PersonaInterna es accesible solo dentro del bloque de la expresión pero no fuera de él==. Esta característica ==permite encapsular el nombre de la clase== y evitar conflictos de nombres.

```js linenums="1"
const Persona = class PersonaInterna {
  constructor(nombre) {
    this.nombre = nombre;
  }

  saludar() {
    console.log(`Hola, soy ${this.nombre}.`);
  }
};

const persona_1 = new Persona('Nerea');
persona_1.saludar(); // Hola, soy Nerea.

// El nombre interno "PersonaInterna" no es accesible fuera de la clase
console.log(typeof PersonaInterna); // undefined
```

### :material-arrow-right-box: Cuándo usar expresión de clase:

  - **Clases dinámicas**: Cuando necesitas ==definir clases de forma condicional o dentro de funciones==.
  - **Mantener el código limpio**: Usa ==clases anónimas si no necesitas referenciar el nombre fuera del bloque==.


<br>

### :material-arrow-right-box: Sintaxis de una clase:

```js linenums="1"
class NombreClase {                       // declaración de clase + nombre de clase
    constructor(atributo_1, atributo_2) { // constructor + atributos
        this.propiedad_1 = atributo_1;    // propiedad de una clase
        this.propiedad_2 = atributo_2;    // propiedad de una clase
    }

    metodo_1() { // se nombra un método
        return (`Devuelve ${this.propiedad_1} y ${this.propiedad_2}`); // cuerpo de método
    }
}

const objeto_1 = new NombreClase('argumento_1', 'argumento_2'); // se crea un objeto pasando argumentos
console.log(objeto_1.metodo_1()); // Salida: Devuelve argumento_1 y argumento_2
```
<br>

### :material-code-braces: Clase + ==constructor==:

```js linenums="1"
class Persona {

    constructor(nombre) {
        this.nombre = nombre;
    }
}

const persona_1 = new Persona('Nerea');
console.log(persona_1.nombre); // Salida: Nerea
```
<br>

### :material-code-braces: Clase + ==constructor== + ==1 método==:

```js linenums="1"
class Persona {

    constructor(nombre) {
        this.nombre = nombre;
    }

    nombrePersona() {
        return (`${this.nombre}`);  
    }
}

const persona_1 = new Persona('Nerea');
console.log(persona_1.nombrePersona()); // Salida: Nerea
```
<br>

### :material-code-braces: Clase ==con llaves== en atributos y argumentos:

```js linenums="1"
class Persona {

    constructor({nombre, apellido}) {
        this.nombre = nombre;
        this.apellido = apellido;
    }

    nombreCompleto() {
        console.log(`${this.nombre} ${this.apellido}`);
    }
}

const persona_1 = new Persona({nombre: 'Markel', apellido:'Martínez'});
const persona_2 = new Persona({apellido: 'Medina', nombre: 'Gorka'});

persona_1.nombreCompleto();
persona_2.nombreCompleto();

/* Salida:

Markel Martínez
Gorka Medina

*/
```
<br>

### :material-code-braces: Clase ==sin llaves== en atributos y argumentos:
```js linenums="1"
class Persona {

    constructor(nombre, apellido) {
        this.nombre = nombre;
        this.apellido = apellido;
    }

    nombreCompleto() {
        console.log(`${this.nombre} ${this.apellido}`);
    }
}

const persona_1 = new Persona('Markel', 'Martínez');
const persona_2 = new Persona('Gorka', 'Medina');

persona_1.nombreCompleto();
persona_2.nombreCompleto();

/* Salida:

Markel Martínez
Gorka Medina

*/
```
***
<br>

## **6.2.1. Método de instancia:**

### Ejemplo 1
En este ejemplo, el uso de **llaves** en **atributos** como en **argumentos** es necesario para poder ==renombrar el valor== predeterminado del **atributo** ==tipo== si diese el caso.

### :material-code-braces: Clase + ==constructor== + ==1 valor de atributo predeterminado==:

  - Se declara una **clase** llamado ==Persona==
  - Se crea un **constructor**, se le pasa ==1 atributo== llamado **tipo** ==con valor predeterminado==, el resto sin valores
  - Se crea un **método** llamado ==descripcion==
  - Se crean 2 **objetos** llamados ==persona_1==, ==persona_2== y se le pasan ==argumentos== a cada uno.

```js linenums="1"
class Persona {

    constructor({tipo = 'alumno', nombre, apellido, edad}) {
        this.tipo = tipo;
        this.nombre = nombre;
        this.apellido = apellido;
        this.edad = edad;
    }

    descripcion() {
        return (`${this.nombre} ${this.apellido} tiene ${this.edad} años y es ${this.tipo}.`);
    }
}

const persona_1 = new Persona({nombre: 'Markel', apellido:'Martínez', edad: 36});
const persona_2 = new Persona({nombre: 'Gorka', apellido: 'Medina', edad: 45, tipo: 'profesor'});

console.log(persona_1.descripcion());
console.log(persona_2.descripcion());

/* Salida:

Markel Martínez tiene 36 años y es alumno.
Gorka Medina tiene 45 años y es profesor.

*/
```
<br>

Veamos éste otro ejemplo con la misma lógica:
```js linenums="1"
class Coche {
    constructor({anio, marca, motorizadoPor = 'gasolina'}) {
        this.anio = anio;
        this.marca = marca;
        this.motorizadoPor = motorizadoPor;
    }

    caracteristicas() {
        return (`El ${this.marca} ${this.anio} funciona con ${this.motorizadoPor}`)
    }
}

const model3 = new Coche({anio: 2025, marca: 'Tesla', motorizadoPor: 'electricidad'});

console.log(model3.caracteristicas());

/* Salida:

El Tesla 2025 funciona con electricidad

*/
```
<br>

Veamos una ==clase sin método== con la misma lógica. ==No se recomienda==, esto implica tener que construir la respuesta completa en cada llamada a la clase, ==se recomienda crear un método dentro de la clase y llamarlo==.

```js linenums="1"
class Coche {

    constructor({marca='Tesla', anio, motorizadoPor = 'gasolina'}) {
        this.marca = marca;
        this.anio = anio;
        this.motorizadoPor = motorizadoPor;
    }
}

const model3 = new Coche({anio: 2025, motorizadoPor: 'electricidad'});

console.log(`El ${model3.marca} ${model3.anio} funciona con ${model3.motorizadoPor}`);

/* Salida:

El Tesla 2025 funciona con electricidad

*/
```
***
<br>

## **6.2.2. Método estático:**
Con un método estático, no requiere crear un objeto mediante instancia para que funcione.

  - **Acceso global**: pueden utilizarse en cualquier lugar del código sin necesidad de crear una instancia de la clase. Esto hace que sean accesibles de manera global y fácil de usar.

  - **Optimización de recursos**: al no requerir la creación de instancias, los métodos estáticos pueden ser más eficientes en términos de recursos.

  - **Mantenimiento simplicado**: cuando un método no necesita acceder a propiedades de instancia, es recomendable definirlo como estático, lo que simplifica el mantenimiento y reduce la complejidad del código.

### :material-code-braces: Clase + ==método estático==:
```js linenums="1"
class Persona {

    static saludo(nombre) {
        return (`${nombre} está saludando`);
    }
}

console.log(Persona.saludo("Gorka"));

/* Salida:

Gorka está saludando

*/
```

### :material-code-braces: Clase + ==método de instancia== + ==método estático==:
Supongamos que estamos construyendo un sistema de gestión de usuarios y necesitamos ==generar un ID único para cada usuario==.

En este caso, ==el **método estático** generarID se utiliza para crear ID únicos sin necesidad de crear una instancia de la clase Usuario==.

```js linenums="1"
class Usuario {
    constructor(nombre) {
        this.nombre = nombre;
        this.id = Usuario.generarID();

    } static generarID() {
        return Math.floor(Math.random() * 1000);
    }
}

const usuario_1 = new Usuario('Nerea');
console.log(usuario_1.id);

/* Salida:

Se genera un número (id) único de forma aleatoria.

*/
```
***
<br>

## **6.2.3. Propiedad estática:**
Además de los métodos estáticos, ==las clases en JavaScript también pueden tener **propiedades estáticas**==, que son variables que pertenecen a la clase en su totalidad y no a las instancias individuales. ==A partir de ES2022 JavaScript permite definir propiedades estáticas de manera más sencilla dentro de la clase==. Esto se hace utilizando la palabra clave **static** antes de la definición de la **propiedad**.

### :material-code-braces: Clase + ==propiedad estática==:
```js linenums="1"
class MiClase {
    static miPropiedadEstatica = "Soy una propiedad estática";
}

console.log(MiClase.miPropiedadEstatica); // Salida: Soy una propiedad estática
```
<br>

En este caso **usuariosMax** es una **propiedad estática** que ==pertenece a la clase **Configuracion**==. Al ser **estática**, ==no puede ser accedida a través de **métodos de instancias** de la clase==.
```js linenums="1"
class Configuracion {
    static usuariosMax = 100;
}

console.log(Configuracion.usuariosMax); // Salida: 100
```
<br>

### :material-arrow-right-box: ==Acceso a propiedades estáticas== desde ==métodos estáticos==:
Los **métodos estáticos** pueden acceder a otras **propiedades** y **métodos estáticos** usando **this**, que en este contexto se refiere a la **clase**.

### :material-code-braces: Clase + ==propiedad estática== + ==método estático== + alcance:
```js linenums="1"
class Calcular {
    static iva = 1.21;
    
    static calcularIva(precioNeto) {
        return (precioNeto * this.iva) + '€ iva incluido';
    }
}

console.log(Calcular.calcularIva(100)); // Salida: 121€
```
<br>

Veamos un ejemplo donde ==combinamos **métodos** y **propiedades estáticas** para modelar un sistema de configuración==.

==version== y ==conexionesMaximas== son **propiedades estáticas** de la **clase** ==Sistema== y el **método** ==obtenerInfo()== proporciona información relevante sobre el sistema

```js linenums="1"
class Sistema {
    static version = '1.0.0';
    static conexionesMaximas = 10;

    static obtenerInfo() {
        return `Versión: ${this.version}, Conexiones máximas: ${this.conexionesMaximas}`;
    }
}

console.log(Sistema.obtenerInfo()); // Salida: Versión: 1.0.0, Conexiones máximas: 10
```

### Buenas prácticas:

  - ==Usa **métodos estáticos** para lógica no específica de instancias==: Ideal para funciones utilitarias, cálculos compartidos o valores constantes.
  - ==Evita abusar de los **métodos estáticos**==: Usa instancias y métodos de instancia cuando necesites trabajar con datos específicos de objetos.
  - ==Organiza las **propiedades estáticas**==: Colócalas al inicio de la clase para mayor claridad.
  - ==Documenta el propósito de los **métodos estáticos**==: Deja claro en los comentarios cuándo y por qué un método debe ser estático.

### Conclusión:
Las propiedades y métodos estáticos son herramientas poderosas para agregar funcionalidades compartidas a las clases en JavaScript. Son útiles para crear funciones utilitarias, mantener valores constantes y manejar estados compartidos. Sin embargo, deben usarse con moderación y no como sustituto de la lógica basada en instancias.
***
<br>

## **6.3. Nombres de propiedad computadas:**
Los nombres de propiedad computadas permiten utilizar una expresión dentro de corchetes (==[ ]==) para definir el nombre de una propiedad. Esto significa que el nombre de la propiedad se calcula en tiempo de ejecución en lugar de ser un valor literal. En el contexto de las clases, estas pueden usarse para definir tanto métodos como propiedades.

Al definir métodos en una clase, los nombres de propiedad son útiles cuando el nombre del método no se conoce hasta tiempo de ejecución.

### Ejemplo 1
En este ejemplo, ==el nombre del **método** se calcula a partir del valor de la variable metodoDinamico==, lo que permite definir métodos de manera más dinámica.

### :material-code-braces: Clase + ==1 método con nombre computado==:

```js linenums="1"
const metodoDinamico = 'mostrarNombre';

class Usuario {
  constructor(nombre) {
    this.nombre = nombre;
  }
  
  [metodoDinamico]() {
    console.log(`Nombre del usuario: ${this.nombre}`);
  }
}

const usuario1 = new Usuario('Kristine');

usuario1.mostrarNombre(); // Salida: Nombre del usuario: Kristine
```
<br>

Los nombres de propiedad computadas son especialmente útiles en los siguientes escenarios:

  1. **Asignación Dinámica de Propiedades o Métodos**: Cuando el nombre de una propiedad o método depende de una entrada del usuario o de otra lógica que se ejecuta en tiempo de ejecución.
  2. **Configuración Basada en Datos Externos**: Si necesitas definir propiedades basadas en un conjunto de datos dinámico, los nombres de propiedad computados facilitan este proceso.
  3. **Evitar Redundancia en Código Repetitivo**: Puedes crear múltiples métodos o propiedades usando un patrón común sin tener que escribir cada uno manualmente.

<br>

### Ejemplo 2
En este ejemplo, ==los **métodos** se definen usando los valores almacenados en el array acciones==, lo que evita la repetición de código y facilita la creación de métodos con nombres similares.

### :material-code-braces: clase + ==métodos con prefijos comunes==:

```js linenums="1"
const acciones = ['Iniciar', 'Detener', 'Reiniciar']; // array

class Maquina {
  constructor(nombre) {
    this.nombre = nombre;
  }
  
  [acciones[0]]() {
    console.log(`${this.nombre} está iniciando.`);
  }
  
  [acciones[1]]() {
    console.log(`${this.nombre} se ha detenido.`);
  }
  
  [acciones[2]]() {
    console.log(`${this.nombre} está reiniciando.`);
  }
}

const servidor = new Maquina('Servidor A');

servidor.Iniciar();   // Salida: Servidor A está iniciando.
servidor.Detener();   // Salida: Servidor A se ha detenido.
servidor.Reiniciar(); // Salida: Servidor A está reiniciando.
```
<br>
Aunque las propiedad computados son una característica poderosa, hay algunas consideraciones importantes a tener en cuenta:

  1. **Legibilidad del Código**: ==El uso excesivo puede afectar la legibilidad del código==. Es importante usarlos cuando realmente agreguen valor.
  2. **Errores de Tipo**: Asegúrate de que la expresión utilizada para calcular el ==nombre de la propiedad sea válida y retorne un **string**. De lo contrario se lanzará un error==.

### Conclusión:
Los nombres de propiedad computadas en clases son una característica útil de JavaScript que permite definir métodos y propiedades de forma dinámica. Cuando se usan adecuadamente pueden simplificar la configuración de objetos y clases, evitar redundancias y hacer que el código sea más flexible. Sin embargo, es importante no abusar de esta técnica para mantener la claridad del código.
***
<br>

## **6.4. Herencia:**
La herencia en JavaScript permite que una clase hija adquiera las propiedades y métodos de una clase base, lo cual facilita la creación de jerarquías de clases. La clase hija puede ampliar o modificar la funcionalidad heredada para adaptarla a necesidades específicas.

### :material-arrow-right-box: Sintaxis de la herencia:
==Para crear una clase que extienda otra clase==, se utiliza la palabra clave **extends**:

En este ejemplo, ==la **clase** Perro extiende la **clase** Animal==, lo que le permite acceder al **método** ==hacerSonido()== de la clase base.
```js linenums="1"
class Animal {
  constructor(nombre) {
    this.nombre = nombre;
  }
  
  hacerSonido() {
    console.log(`${this.nombre} está haciendo un sonido.`);
  }
}

class Perro extends Animal {
  ladrar() {
    console.log(`${this.nombre} está ladrando.`);
  }
}

const miPerro = new Perro('Rex');

miPerro.hacerSonido(); // Salida: Rex está haciendo un sonido.
miPerro.ladrar();      // Salida: Rex está ladrando.
```

### Beneficios de la Herencia:

  1. **Reutilización del Código**: Se evita la duplicación al reutilizar el comportamiento común definido en la clase base.
  2. **Extensión de Funcionalidades**: La clase hija puede añadir características o cambiar el comportamiento de los métodos heredados.
  3. **Organización y Mantenimiento**: Ayuda a estructurar el código en niveles jerárquicos, haciendo más fácil comprender y mantener la lógica.
***
<br>

#### Editor de código utilizado:

  - [Programiz - JavaScript Online Compiler :octicons-link-external-24:](https://www.programiz.com/javascript/online-compiler/){:target="_blank"}

<br>
<br>
