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
