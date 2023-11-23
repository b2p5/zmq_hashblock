
# Ejemplo de utilización la biblioteca ZeroMQ con hashblock 

1. **Crear un contexto zmq**: El programa comienza creando un nuevo contexto ZeroMQ. Este contexto se utiliza para crear sockets ZeroMQ.

2. **Crear un socket de tipo SUB**: El programa crea un socket SUB utilizando el contexto ZeroMQ. Si hay un error al crear el socket, el programa imprime el error y lo devuelve.

3. **Conectar al nodo Bitcoin**: El socket SUB se conecta a un nodo de Bitcoin que se ejecuta en localhost en el puerto 28332. Si hay un error al conectar, el programa imprime el error y lo devuelve. 
En el archivo ***bitcoin.conf*** se ha de incluir el comando: 
zmqpubhashblock=tcp://127.0.0.1:28332

4. **Suscribirse a eventos relacionados con la mempool**: El socket SUB se suscribe a los eventos "hashblock", que representan las notificionrs sobre todas las transacciones.

5. **Recibir y procesar mensajes**: El programa entra en un bucle donde recibe y procesa continuamente mensajes. El primer mensaje que recibe es el canal de suscripción, que descarta. El segundo mensaje que recibe es el hash del bloque de 32 bytes, la cual se pasa a string. La tercera parte es un numero de secuencia. Si hay un error al recibir cualquiera de los mensajes, el programa imprime el error y continúa con la siguiente iteración del bucle o devuelve el error.

6. **Pausa**: El programa hace una pausa de 2 segundos para evitar el consumo excesivo de recursos.



*Resultado del script:*

Hash: "00000000000000000000324a0860e13066d7beed9785d47523b46a64b6f380e8"

Topic: "hashblock"

Sequence number: 09000000 -> "\t\0\0\0"


