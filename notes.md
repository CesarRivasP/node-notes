Notas
- Siempre que se vaya a aplicar un comando que tenga la bandera '-g', indica que ese paquete (con npm)
se va a aplicar globalmente, por lo que se debe ser administrador super usuario del equipo

Librerías
- Nodemon: funciona como un servidor de desarrollo, nos permite realizar cambios y que se actualicen en tiempo real
  * mediante rs se reinicia todo el proceso de nodemon, y se ejecuta de nuevo todo el programa

Require
Hay tres tipos de require:

1.- De un proyecto propio en node, es decir, solo definimos dicha librería porque la misma es nativa de node
const fs = require('fs');   

2.- No es una libreria que es propia de node, es decir, es un paquete que se instala para su posterior utilización. No nativo de node, son expansiones, etc
const express = require('express');

3.- Archivos que creamos en el proyecto, se identifican en el proyecto, se identifican como ('./PATH')
const fs = require('fs');


- Existe un objeto global que se llama 'module' el cual posee una serie de atributos como el id, una parte de exportaciones que es como un lugar en donde se pueden poner objetos para que sean trabajados de forma global, el path de donde se esta ejecutando el archivo, entre otras cosas.
El modulo es un objeto global que esta disponible a lo largo de toda la aplicación

- Otro de los objetos globales se llama 'process', no hay que definirlo en ningún lugar, puesto que node al ejecutarse crea dicha variable de entorno.
* Este objeto global se encuentra corriendo a lo largo de toda la aplicacion de node.
* Tambien, este objeto es actualizado dependiendo del entorno en el que se encuentre corriendo
En el process hay una parte muy importante llamada argumentos 'argv', los cuales son dos:
  - La ubicación de node
  - La ubicación del archivo que se esta utilizando (path)
Nota: A la hora de ejecutar comandos que reciben argumentos, cada vez que se le agregan argumentos, cada uno de los argumentos adicionales lo recibe el argv.

- El npm init proporciona una guia para la creacion del package.json  
  * Puede tener cualquier nombre siempre que sea URL friendly (sin espacios, sin mayúsculas)
  * El entry point es el primer archivo de node que se ejecuta y después despliega el resto de la aplicación
  * El package-lock.json es un registro de todo lo que se hizo para poder tener instalados cada uno de los paquetes que se tienen como dependencias en el package.json
  * Todo lo que esta en node_modules son plugins y paquetes necesarios para que las dependencias que tenga definidas el proyecto. Por lo general no es enviado a los módulos de producción ni repositorios de git, solo basta tener el package.json para que al realizar un npm install se descarguen todos los paquetes y plugins necesarios para la ejecución del proyecto.
    + No es recomendable subir los node_modules a los repositorios de git porque las librerías que este contiene pueden variar dependiendo del sistema operativo
Nota: Si se instalan paquetes de forma local, y no de manera global, no se van a ocupar privilegios de superusuario porque va a estar corriendo localmente en el proyecto indicado


Libreria Yargs
En el método command va a contener 3 argumentos:
  - Nombre del comando
  - Información para mostrar el usuario
  - Es un objeto que va a recibir la configuración de parámetros (flags) que ese comando puede recibir


- Tanto la librería request como axios se encargan de lo mismo, trabajan con peticiones hacia servicios REST.
La principal diferencia es que axios trabaja en base a promesas y request en base a callbacks

Status de las peticiones
- 200: se hizo correctamente
- 404: no encontró el url
- 500: error del servidor

- Un Bad Request quiere decir que se solicito mal la información, se realizo la llamada al servicio mal

Public
Aquí se encuentra la información o el contenido que puede ser visto por cualquiera.
Todo archivo dentro de esa carpeta automáticamente queda siendo disponible para cualquier persona

HTTP
- El paquete http nativo de node, nos permite crear web servers listos para desplegar contenido en la web
- Al trabajar con este server, escucha todas las peticiones sin importar de que url sean

EXPRESS
- Internamente usa el modulo http nativo de node
- Internamente la función 'send' va a detectar que es un objeto, y lo va a serializar en formato JSON
- Al trabajar en express se puede crear un middleware que permite filtrar cualquier tipo de petición

Middleware
Es una instrucción o un callback que se va a ejecutar siempre, no importa que url es el que se este pidiendo

Paquete hbs
Este paquete le va a permitir a express poder renderizar las paginas que usan la sintaxis de handlebars y poderle mandar una respuesta al cliente de manera que nuestro sitio web sea dinámico

Parciales
Es un lote de codigo html que se puede reutlizar

dirname
Indica que no importa el path en el que se encuentre, deebe tomar ese path (es una variable global) y concatenale la siguiente ruta
```
(__dirname, '/views/partials')
```

Banderas para node
-e para que este pendiente de los archivos indicados por medio de su extensión

Helpers del hbs
Es una función que se dispara cuando el template lo requiere

Peticiones GET
Se suele utilizar para obtener los datos

Peticiones POST
Es muy utilizado para crear registros
- Normalmente no solo se realiza la petición, si no que también hay que mandar información

Peticiones PUT
Es muy utilizado cuando lo que se quiere es actualizar data
* Por lo general, a la hora de hacer una actualización esta se realiza por la Url. Para que este tipo de petición acepte la url hay que especificar el path.
Nota: El método PATCH y el PUT son manejados de la misma manera

Peticiones DELETE
* En las bases de datos ya no se acostumbra borrar registros, por lo que se acostumbra en una petición delete solamente cambiar el estado de algo para que ya no este disponible, pero el registro siempre queda

body-parcer
Este paquete permite procesar la información de la petición post que se este enviando desde la aplicación al servidor, y la serializa en un objeto json para que sea fácilmente procesada en las peticiones post

- Los app.use son middlewares, funciones que se van a disparar cada vez que la ejecución pase por su linea de ubicación

Status 400
Este error es producto de que no se envió la información como el servicio la espera

Conexión con MongoDB
- Si al indicar la ruta de conexión con la base de datos a la que esperamos acceder, aunque esta base de datos no ha sido creada, se puede hacer una conexión perfectamente. Y cuando se realicen inserciones a esta base de datos (que no existe) mongoose y mongo van a crear toda la estructura necesaria para funcionar
- Se puede utilizar robo3t como manejador de bases de datos para mongoDB localmente
- Para conectarse al mongoDB Atlas o en general a las bases de datos mongo se puede utilizar mongoDB Compass

Modelo del usuario
Un modelo es un objeto de mongoose que nos va a permitir realizar inserciones, actualizaciones, trabajar con funciones ya creadas por el equipo de mongo que nos otorgan facilidades y crear funciones personalizadas por nosotros.

Encriptacion
Método hash de una sola vía
Este método permite que si el usuario o un tercero obtiene toda la cadena de caracteres creada, no va a ser posible construirla a la versión anterior o a su forma original.
El paquete a usar es bcrypt
  - hashSync: hace el hash de forma sincrona, es decir, sin necesidad de usar un callback, promesa, etc. Lo realiza directamente.
    hashSync(data a almacenar, numero de vueltas que se quiere aplicarle a el hash)

Underscore
Es una librería que expande js con muchas funcionalidades que debería tener por defecto
* pick
Devuelve una copia del objeto, filtrando solo los valores que se quieren.

mLab
Es un servicio gratuito de hasta 500 mb
- Posteriormente se aliaron con mongodb en lo que deriva MongoDB Atlas

Tokens
Tanto físicos como virtuales, ambos funcionan para la misma tarea
Virtuales
Al ingresar a una plataforma y se quiere realizar alguna transacción, nos solicitaran estos números, mejor conocidos como un token. Una vez introducido el token nos va a permitir realizar una determinada tarea, ya que esta es una autorización de dos pasos:
1.- El paso para autenticarnos en la plataforma
2.- Luego, este token que esta asociado con nuestra cuenta. Por lo que si se quisiera acceder a nuestra cuenta, necesitarían tanto el token como la clave física.
- En el curso se va a trabajar con un formato de tokens que son semejantes a un JSON web token.

¿Por que usar tokens?
- Variables de sesión
Las aplicaciones utilizan estas variables para manejar la autenticación de los usuarios
* Una variable de sesión se crea cuando un usuario se autentica correctamente en nuestra aplicación
* Son muy utilizadas en aplicación de hasta unos 5000 a 10000 usuarios mas o menos, y mediante estas se dificulta el acceso simultaneo de un usuarios desde diferentes equipos
Para resolver ese problema de las variables de sesión se utilizan los:
Tokens
- Hay varios tipos de tokens de diferentes formatos
- La estructura de Json Web Token (JWT) esta dividido en tres partes:
  + Header: usualmente se visualiza como la parte inicial y roja del token, y esta contiene información sobre el algoritmo utilizado para la encriptacion junto con el tipo de token. En este caso un JWT
    - HS256: ese algoritmo es una encriptacion de doble vía, quiere decir, que aunque parezca que esta segura la información, la parte del payload es totalmente visible y si alguien obtiene ese token, podria ser capaz de poder obtener el payload, la fecha de emision, expiracion y otras cosas.
    Esto no garantiza que la información esta encriptada de una forma totalmente segura
  + Payload: Contiene la información que se quiere que este en el token. Aunque este parezca que esta encriptado,
  es sencillo obtener el código
  + Firma: permite a los verificadores de Json Web Token constatar si el token es valido. Es decir, se va a firmar el token de manera que si la persona no sabe exactamente como fue que se construyo los tokens falsos, no van a poder pasar la validaciones que se van a colocar en el lado del backend server.
  El token es algo que va a existir en cada una de las computadoras clientes. Las computadoras clientes todas van a tener un token único totalmente diferente. Claro, la estructura es parecida, pero el contenido del mismo es único, por lo que si cada una de esas maquinas se quiere conectar a la aplicación que estaría montada en un servidor, y quieren obtener información de algún servicio, y este requiere alguna autenticación, va a pedir el token. Si no se suministra el token el servidor no mandara la información.
  La validacion se realiza en el momento.
  En la parte de la firma es algo que se debe configurar en el backend para que de esa manera se puedan recibir los tokens y nos aseguremos que esos tokens no fueron manipulados y si lo fue se pueda detectar el cambio y que este no sea un token valido para la aplicacion

Practica
  ```
function parseJwt (token) {
    var base64Url = token.split('.')[1];
    var base64 = base64Url.replace('-', '+').replace('_', '/');
    return JSON.parse(window.atob(base64));
};
  ```
Nota:
**NO se debe de usar para validar tokens, no es el código ideal para eso, es un código para extraer información de un token desde el Front-End. NO USAR EN EL BACKEND**

Local Storage
En el navegador, la pestaña de aplicación tiene una sección llamada **Local Storage**, en la cual se almacena información como las cokies, también se puede grabar información para que permanezca persistente en el equipo.
Normalmente el Local Storage comparte información por dominio, es decir, cuando estemos en otro dominio va a tener otra información almacenada.
- Esta parte es totalmente manipulable por parte del cliente
- Aquí también se encuentra información del token, el cual esta del lado del cliente y el cliente lo puede observar
Sesion Storage
Es similar al Local Storage, pero este se borra cuando se cierra el navegador web, el local storage permanece aunque reiniciemos la maquina, queda persistente.
Nota:
Los tokens son encriptados de doble via, por lo que hay maneras de obtener la información que contienen. Dicho esto, es importante que en los tokens no se guarde información sensible, como lo puede ser la contraseña del usuario, ya que esta queda totalmente visible. Si esta encriptado de una sola vía, va a ser muy complicado obtener la información, pero de igual manera se le estaría dando información que el usuario final no necesita
La firma es la parte mas importante cuando se trabaja en la parte de node, porque si la firma no coincide con lo que nosotros generamos, ese token debe ser ignorado ya que fue manipulado por el usuario.
