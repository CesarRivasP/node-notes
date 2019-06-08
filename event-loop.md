## Event Loop - Ciclo de eventos de Node
Es el ciclo de vida que tiene node al ejecutar un programa

### Ciclo de vida de un proceso

#### App1
* Ejecuta el proceso main()
* Coloca en la pila de procesos la primera linea de código y luego lo elimina
  + Y así sucesivamente va a realizar dicha acción con las siguientes lineas de código
  + Ejecuta y elimina de la pila de procesos
* Cuando ya no hay nada en la pila de procesos, node termina el proceso main()

#### App2
* Se crea el main() y se empieza a ejecutar
  + El main contiene todo el código que se encuentra en el app2.js
* Registra la función greet
* Pasa a la siguiente linea (no ejecuta la función)
  let greeting = greet('name') //dispara la función greet
* Cuando la función se dispara, y ya esta en la pila de procesos node empieza a trabajar con la función, por lo que ejecuta la primera linea de la función. Así sucesivamente hasta que ejecuta la ultima linea (return), y allí la función termina.
Al terminar la función se quita de la pila de procesos
* Pasa al console.log, lo ejecuta y lo borra de la pila de procesos
* Se elimina el main

#### App3
- Los procesos en node van de:
```
Pila de procesos (Call Stack) -> Node Apis -> Cola de Callbacks
```
* Crea el main
* Ejecuta y quita de la pila la primera linea de código
* Coloca en la pila el primer setTimeout y lo registra
  + Solo lo registra, no lo ejecuta aun porque se debe de ejecutar después de 3 segundos. Esta seria la primera tarea asincrona
  + Como solo la registra, mas no la elimina porque aun no esta resuelta, y pasa esa instrucción a Node Apis
    # Node Apis es un lugar en donde node esta pendiente de esos procesos y en este caso espera respuestas, tareas asíncronas como esta, esperando los tres segundos para ejecutarla, entre otras
    acciones. Aquí corren simultáneamente distintas tareas
  + Esa tarea se queda en node apis, mientras que la funcion no llegue a los 3 segundos se va a quedar alli esperando
* Coloca en la pila el segundo setTimeout y lo registra. Esta a 0 segundos, pero eso no quiere decir que inmediatamente se va a ejecutar
  + Al registrarlo lo pasa a node apis
* Coloca en la pila el tercer setTimeout y lo registra
  + Al registrarlo lo pasa a node apis
* Una vez transcurra el tiempo para que se ejecute alguno de los timeouts, lo manda a la cola de callbacks
  # La cola de callbacks son todos los procesos que ya están listos para ser ejecutados, pero hay que esperar que la pila de procesos que corre node actualmente termine. La cola de callbacks se ejecuta mediante van llegando los procesos. El primero que llega es el primero en salir
  + Mientras tanto, la cola de callbacks va a esperar su momento para ser ejecutada
* Por ultimo en la función main, llegan al ultimo console.log, lo agrega a la pila, lo ejecuta y lo elimina
  + Como no es una tarea asíncrona o algo parecido, entonces la ejecuta y se termina
* Como ya no hay nada en el main, por lo cual el main termina
* Node revisa las pilas, por lo que al revisar que no hay procesos en el call stack, pero si hay callbacks en espera, va a realizar las siguientes acciones:
 - tomar la primera instrucción que se encuentre en la cola
 - La pasa a la pila de procesos
 - Ejecuta y borra
 * Y repite esta acción mientras hayan instrucciones en la cola de callbacks
 * Para que los timeouts pasen a la cola de callbacks tuvo que haber pasado el tiempo indicado en la función
* Cuando node detecta que no hay nada en la pila de procesos, node api, y cola de callbacks, entonces allí termina nuestro proceso.
  # Lo que sale de node apis pasa a la cola de callbacks porque es la manera en que javascript realiza todo en secuencia
