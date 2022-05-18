![logotipo de The Bridge](https://user-images.githubusercontent.com/27650532/77754601-e8365180-702b-11ea-8bed-5bc14a43f869.png  "logotipo de The Bridge")


# [Bootcamp Web Developer Full Stack](https://www.thebridge.tech/bootcamps/bootcamp-fullstack-developer/)
### JS, ES6, Node.js, Frontend, Backend, Express, React, MERN, testing, DevOps

## Clase 20

### API REST

![img](../../assets/back/clase20/express.png)

### Teoría - API REST

![WideImg](../../assets/back/clase20/rest.png)

API es un conjunto de reglas y especificaciones que las aplicaciones pueden seguir para comunicarse entre ellas. Para que lo entendamos, el uso de una API es el mecanismo más útil para conectar dos softwares entre sí, de esta manera, podemos garantizar el intercambio de mensajes o datos en formato estándar.

Las operaciones más importantes relacionadas con los datos en cualquier sistema REST y la especificación HTTP son cuatro; POST (crear), GET (leer y consultar), PUT (editar) y DELETE (borrar).

Rest, que es la abreviación de Representational State Transfer, es un conjunto de restricciones que se utilizan para que las solicitudes HTTP cumplan con las directrizes definidas en la arquitectura.

![WideImg](../../assets/back/clase20/restapi.jpeg)
![WideImg](../../assets/back/clase20/restapi2.png)
![WideImg](../../assets/back/clase20/restapi3.png)

Ejemplos de peticiones:
```javascript
HTTP GET http://www.appdomain.com/users
HTTP GET http://www.appdomain.com/users?size=20&page=5
HTTP GET http://www.appdomain.com/users/123
HTTP GET http://www.appdomain.com/users/123/address
HTTP POST http://www.appdomain.com/users
HTTP POST http://www.appdomain.com/users/123/accounts

HTTP PUT http://www.appdomain.com/users/123
HTTP PUT http://www.appdomain.com/users/123/accounts/456

HTTP DELETE http://www.appdomain.com/users/123
HTTP DELETE http://www.appdomain.com/users/123/accounts/456
```
Más sobre API REST:
- [que-es-api-rest-integrar-negocio-business-tech](https://www.iebschool.com/blog/que-es-api-rest-integrar-negocio-business-tech/)
- [api-rest](https://rockcontent.com/es/blog/api-rest/)
- [a-beginners-guide-to-http-and-rest](https://code.tutsplus.com/es/tutorials/a-beginners-guide-to-http-and-rest--net-16340)
- [Ejemplos de peticiones REST](https://restfulapi.net/http-methods/)

### Crear una API REST con Express
- [routing-with-express-and-postman](https://iq.opengenus.org/routing-with-express-and-postman/)
- [nodejs-express-routing](https://www.digitalocean.com/community/tutorials/nodejs-express-routing)
- [building-a-node-js-rest-api-with-express](https://medium.com/@jeffandersen/building-a-node-js-rest-api-with-express-46b0901f29b6)
- [desarrollando-una-sencilla-api-rest-con-nodejs-y-express](https://asfo.medium.com/desarrollando-una-sencilla-api-rest-con-nodejs-y-express-cab0813f7e4b)

### EJERCICIOS - API REST con Express

1. Modificar la BBDD del ejemplo de clase para que no se puedan insertar entries repetidas por título.

2. Completar la API del back de clase con las siguientes rutas:

- [GET] http://localhost:3000/api/entries

Modificar la query SQL para que me devuelva una respuesta con los datos del autor y sin ID de la entry:

```javascript
{
"title": "noticia desde Node",
"content": "va a triunfar esto2",
"date": "2022-03-20T23:00:00.000Z",
"category": "sucesos",
"name": "Alejandru",
"surname": "Regex",
"image": "https://randomuser.me/api/portraits/thumb/men/75.jpg"
},
```
En vez de esta respuesta, que es la que está ahora:
```javascript
 {
"id_entry": 2,
"title": "Noticia: Un panda suelto por la ciudad",
"content": "El panda se comió todas las frutas de una tienda",
"date": "2022-03-15T23:00:00.000Z",
"email_author":"alvaru@thebridgeschool.es"
"category": "Sucesos"
},
```
- [PUT] http://localhost:3000/api/entries/ (parecido a POST) modifica una entry por completo con nuevos datos y retorna un status 200. Buscar por título para editar entry.
- [DELETE] http://localhost:3000/api/entries/ Borra una entry y retorna un status 200. Búsqueda por título de entry para borrar. Payload {message: "Se ha borrado la entry 'Título de noticia' "}

![img](../../assets/back/clase20/restapimeme.jpg)

3. Crea una aplicación de películas para hacer una API REST con Express. Para ello usa la API de pelis que te proporcionamos
- [OMDB api](http://www.omdbapi.com/)

OJO!: Crea desde cero un repositorio en GitHub para hacer el ejercicio

Rutas:
- [GET] `http://localhost:3000/api/film/:title` Retorna un JSON con los detalles de la peli en concreto buscada. Payload  `{titulo:"Titanic", autor:"James Cameron", descripción:"xxx", src:"titanic.png",etc...}`
- [POST] `http://localhost:3000/api/film/` Se envía por POST los datos de la película a crear y retorna un status 200. Payload `{message: "Se ha guardado Titanic"}`
- [PUT] `http://localhost:3000/api/film/` Actualiza los datos de una película y retorna un status 200. Payload {id:"0", message: "Se ha actualizado Titanic"}
- [DELETE] `http://localhost:3000/api/film/` Borra una película y retorna un status 200. Payload `{id: "0", message: "Se ha borrado Titanic"}`
- En caso de ruta no encontrada o error, devolver un mensaje de error. Especificar si ha sido un 404, 500, etc...
 - [error-handling](https://expressjs.com/es/guide/error-handling.html)
 - [how-to-handle-404-and-500-errors-on-expressjs](https://davidburgos.blog/how-to-handle-404-and-500-errors-on-expressjs/)

Estructura del proyecto:
- Guarda en otro módulo dentro de la carpeta `utils` (hay que crearla) el código para hacer fetch de la peli. Importa dicho módulo para usarlo en el sitio adecuado...
- ¿Cansado de publicar tus API_KEY privadas al mundo exterior cuando subes tu código a GitHub? Prueba a crearte un fichero `.env` en el que pongas tus claves privadas y añade a `.gitignore` la directriz para ignorar el fichero `.env` al subir a GitHub.
- [https://www.npmjs.com/package/dotenv](https://www.npmjs.com/package/dotenv)
- [environment-variables](https://medium.com/the-node-js-collection/making-your-node-js-work-everywhere-with-environment-variables-2da8cdf6e786)


4. Habilitar rutas para autores en el servidor del ejemplo de clase (Opcional):

- [GET] http://localhost:3000/api/authors Retorna un objeto con los datos de todos los autores. Retorna un status 200
- [GET] http://localhost:3000/api/authors?email=birja@thebridgeschool.es Retorna un objeto con los datos del autor buscado. Retorna un status 200
- [POST] http://localhost:3000/api/authors/ Se envía por POST los datos del autor a crear y retorna un status 201. Payload `{message: "usuario creado: muchelle@thebridgeschool.es"}`
- [PUT] http://localhost:3000/api/authors/ Actualiza los datos de un autor y retorna un status 200. Payload `{message: "usuario actualizado: muchelle@thebridgeschool.es"}`
- [DELETE] http://localhost:3000/api/authors/ Borra un autor y retorna un status 200. Búsqueda por email. Payload `{message: "Se ha borrado muchelle@thebridgeschool.es"}`