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
