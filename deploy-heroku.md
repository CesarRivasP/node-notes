## Deploy en Heroku
1.- Agregar en los scripts del package.json el start para la ejecución del programa
2.- heroku login

### Por la terminal
- heroku create
- git push heroku master


### Por interfaz grafica
- heroku git:remote -a <<name-app>>
- git push heroku master
- heroku open

### Para visualizar variables de entorno de Heroku
```
heroku config
```

### Para agregar variables de entorno a Heroku
```
heroku config:set <name>=<"text">
```

### Para obtener el valor de las variables de entorno a Heroku
```
heroku config:get <name var>
```

### Para borrar una variable de entorno en Heroku
```
heroku config:unset <name var>
```

### Para proteger una URL cuando esta sea una variable de entorno de heroku en git
```
heroku config:set MONGO_URI=<"URL">
```
Luego realizar un **heroku config** para verificar si se creo la variable.
- Sustituir la ruta en el archivo de configuracion por la variable de entorno de heroku, teniendo en cuenta que esta solo se activa cuando se esta corriendo en produccion (sobre heroku)
