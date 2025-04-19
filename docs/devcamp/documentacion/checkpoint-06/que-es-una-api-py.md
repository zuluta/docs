---
hide:
  #- navigation
  #- toc
---

# 5. ¿Que es una API?

<p>Una <strong>API</strong> es una (interfaz de programación de aplicaciones) que sigue un conjunto de restricciones arquitecturales basadas en HTTP. Esto significa que se puede acceder a los recursos a través de URLs, lo que hace que la API sea fácil de entender y utilizar. Podemos crear una API que haga literalmente cualquier cosa, desde dar clima hasta un catálogo completo de una tienda en línea. Casi todas las aplicaciones utilizan APIs para conectarse con fuentes de datos corporativas, servicios de datos de terceros u otras aplicaciones.</p>


!!! tip "TIP"
    El formato de intercambio de datos normalmente es JSON o XML, lo que permite que la API sea compatible con una amplia variedad de aplicaciones.
<br>

![Image](../../../assets/images/devcamp/checkpoint-06/api-rest.png)
<br>
<br>

### 5.1. Una API tiene dos componentes principales:

  - **Recursos:**

    - Datos o información.

  - **Verbos HTTP:**

    - `GET` para consultar y leer.
    - `POST` para crear.
    - `PUT` para editar.
    - `DELETE` para eliminar.

!!! info "IMPORTANTE"
    Los <strong>recursos</strong> son los datos o información que se pueden acceder a través de la API. Los <strong>verbos HTTP</strong> son las operaciones que se pueden realizar en esos recursos, como obtener <code>GET</code> un recurso, crear <code>POST</code> un recurso, actualizar <code>PUT</code> un recurso o eliminar <code>DELETE</code> un recurso.
<br>

### 5.2. ¿De donde obtiene la API toda la información?

<p>La información de la api no sale de la nada, necesita ser construido por alguien en formato diccionario. Se puede construir de manera manual o cargarle la información desde una base de datos. Cuando abrimos la url donde esta alojado el API, veremos un monton de datos en formato diccionario <code>{...}</code>. Puede contener anidamientos tanto de diccionarios como de listas en su interior.</p>

Formato de una API 👇
```json
{
  "id": 1,
  "nombre": "Juan",
  "apellido": "Garcia",
  "pais": "España"
},
{
  "id": 2,
  "nombre": "Nerea",
  "apellido": "Larralde",
  "pais": "España"
}
```

!!! tip "TIP"
    Puedes practicar con esta <strong>API de Rick and Morty</strong> https://rickandmortyapi.com/api/character/ utilizando la aplicación <strong>Postman</strong> https://www.postman.com/ para testear con APIs.

    Si accede a `https://rickandmortyapi.com/api/character/131` por numero de id al personaje, nos devolvera un json con toda la información.
<br>

### 5.3. ¿Qué es Postman?

<p>Se trata de una herramienta dirigida a desarrolladores web que permite realizar peticiones HTTP a cualquier API. Postman es muy útil a la hora de programar y hacer pruebas, puesto que nos ofrece la posibilidad de comprobar el correcto funcionamiento de nuestros desarrollos.</p>

<p>Con esto no queremos decir que Postman sea una herramienta exclusiva para profesionales del entorno web, de hecho va a ser muy útil para todo aquel que tenga que interactuar con una API.</p>

### Características principales:

  - **Envío de solicitudes:**

    - Postman permite enviar solicitudes HTTP y HTTPS utilizando métodos como GET, POST, PUT y DELETE, entre otros. Los desarrolladores pueden especificar parámetros, encabezados y el cuerpo de la solicitud para simular diversas interacciones con una API.

  - **Pruebas automatizadas:**

    - Con Postman, los desarrolladores pueden crear y ejecutar pruebas automatizadas para verificar el comportamiento de una API. Esto ayuda a detectar errores de manera temprana y a garantizar que el software cumpla con los estándares de calidad.
<br>

!!! tip "TIP"
    API de testeo https://rickandmortyapi.com
<br>
<br>
