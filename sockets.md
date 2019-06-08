## ¿ Por que usar Sockets ?
Si se quiere obtener información de la maquina cliente al servidor normalmente se realiza una petición http.get y decirle al servidor que retorne la información que se le esta pidiendo. El servidor le va a responder al cliente mediante una respuesta, y con esa respuesta el cliente realiza una determinada acción. Posteriormente puede que el servidor detecte que dicha información fue actualizada o alterada, en fin, se realizaron cambios. Allí el servidor no va a ser capaz de indicarle a la maquina cliente que hay una nueva información que puede ser de interés, el servidor no es capaz de realizar esa acción directamente hasta que el cliente vuelva a hacer una solicitud http.get para obtener la información.
Si se quisiera establecer una comunicación con otra computadora sea un mensaje privado por ejemplo, la maquina 1 primero tiene que mandar el mensaje al servidor y el servidor determinar a que usuario se lo va a enviar y después enviar el mensaje.
De utilizar la arquitectura vieja, cada cliente tendría que realizar petición http.get constantemente para ver
si hay nuevos mensajes para ellos.
Lo que se busca es que el servidor pueda disparar notificaciones indicando que hay información nueva que le interesa a un usuario en particular. Básicamente, eso son los **Sockets**.
## Sockets
Un socket permite mantener una comunicación activa entre la maquina cliente y el servidor. Es decir, que el servidor va a ser capaz de dispararle notificaciones a la maquina cliente, y la maquina cliente puede interactuar con lo que sea que le responda el servidor. Por lo general se puede mandar Strings, Booleanos, números o un objeto completo. Esto permite al cliente ser notificado en tiempo real cuando algo sucede.
También te permite ser notificado cuando un usuario se conecta o desconecta, y cuando se vuelve a conectar.
También permite disparar eventos personalizados, y esa es una característica que hace de los sockets flexibles.

### Implementacion con express
Socket.io no trabaja directamente con express, pero si trabaja con un servidor http que trae por defecto node


Si al ingresar:
`http://localhost:3000/socket.io/socket.io.js`
Se puede visualizar el código fuente de la libreria, es porque se tiene correctamente configurado socket.io en la parte del backend.
Una vez se pueda visualizar dicho archivo, hay que configurar el frontend para que lo utilice. Este tiene la configuración para trabajar con el backend y mantener una comunicación abierta entre ambos lugares.
