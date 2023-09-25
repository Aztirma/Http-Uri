# HTTP y URI


# **[Comprendiendo Request y Response](https://github.com/kapumota/Desarrollo-software-2023/blob/main/Semana4/Http-URI.md?classId=a1bdca4c-128c-4417-a816-076ce4107fd5&assignmentId=8d2318ef-8255-4a0a-908f-fb661c64fd86&submissionId=b5efbf24-7c8f-6a5b-d059-57d0f281874f#comprendiendo-request-y-response)**

Primero se procedio a hechar un vistazo al contenido de la pagina web señalada en la actividad, la cual trabajaremos en funcion de ella para distintas “operaciones”?

![Untitled](HTTP%20y%20URI%2099a899bef0ef4873bd1d43e4ab6b6fb9/Untitled.png)

El objetivo de esta actividad es el uso de de las herramientas de lineas de comandos curl y nc.

Es por eso que empezaremos haciendo uso del comando curl en nuestro terminal.

![Untitled](HTTP%20y%20URI%2099a899bef0ef4873bd1d43e4ab6b6fb9/Untitled%201.png)

Como se puede observar el uso de este comando mismo nos permito obtener datos del servidor web, esta información es la respuesta HTML que recibe del servidor web.

Siguiendo con la actividad, el siguiente paso será guardar el contenido obtenido en un archivo llamado *pagina_random_words.html* como se observa a continuación:

![Untitled](HTTP%20y%20URI%2099a899bef0ef4873bd1d43e4ab6b6fb9/Untitled%202.png)

Una vez guardado nuestro archivo en nuestro ordenador, abriremos el archivo para obtener una vista previa ???????

![Untitled](HTTP%20y%20URI%2099a899bef0ef4873bd1d43e4ab6b6fb9/Untitled%203.png)

**Pregunta: ¿Cuáles son las dos diferencias principales que has visto anteriormente y lo que ves en un navegador web 'normal'? ¿Qué explica estas diferencias?**

Cuando accedemos al archivo a través de nuestro navegador podemos observar que no se observa la imagen que si aparece cuando acedemos en nuestro navegador web “normal”. La diferencia se debe a que **`curl`** solo muestra el contenido HTML de la página y no carga activamente recursos externos como imágenes.

Además que al solo guardar una respuesta del servidor tan solo muestra una palabra, en ese caso unusual, en cambio al momento de recargar la pagina en el navegador web “normal” esta si cumple la funcion de generar palabras aleatorias continuamente, cosa que el archivo que guardamos tan solo genera. Esta diferencia se debe a que el servidor web que responde a la solicitud de **`curl`** proporciona una sola palabra en la respuesta, mientras que el navegador web "normal" está diseñado para interactuar con la página y solicitar nuevas palabras aleatorias de forma periódica.

Siguiendo con la actividad, ahora se procedera a hacernos pasar por un servidor Web escuchando el puerto 8081: `nc -l 8081`.

![Untitled](HTTP%20y%20URI%2099a899bef0ef4873bd1d43e4ab6b6fb9/Untitled%204.png)

**Pregunta: Suponiendo que estás ejecutando curl desde otro shell ¿qué URL tendrás que pasarle a curl para intentar acceder a tu servidor falso y por qué?**

Para acceder a nuestro servidor falso tendremos que usar la siguiente URL: [http://localhost:8081](http://localhost:8081) ya que aljshdjkadghj

Ahora accederemos a nuestro servidor “falso”, este recibira la solicitud de cliente HTTP.

![Untitled](HTTP%20y%20URI%2099a899bef0ef4873bd1d43e4ab6b6fb9/Untitled%205.png)

Podemos observar que al momento de acceder a nuestro servidor falso, en la ventana donde ejecutamos el ncat, 

**Pregunta: La primera línea de la solicitud identifica qué URL desea recuperar el cliente. ¿Por qué no ves `http://localhost:8081` en ninguna parte de esa línea?**

Por que es redundante , ya que el cliente envía una solicitud en su propia maquina(localhost) en el puerto especifico, por eso no necesita especificar la URL completa en la solicitud. El servidor ya sabe que está en "localhost" y en el puerto "8081" debido a cómo se configuró previamente, por lo que no es necesario repetirlo en la solicitud.

Prueba `curl --help` para ver la ayuda y verificar que la línea de comando `curl -i 'http://randomword.saasbook.info'` mostrará ambos (BOTH) encabezados de respuesta del servidor y(AND) luego el cuerpo de la respuesta.

![Untitled](HTTP%20y%20URI%2099a899bef0ef4873bd1d43e4ab6b6fb9/Untitled%206.png)

**Pregunta: Según los encabezados del servidor, ¿cuál es el código de respuesta HTTP del servidor que indica el estado de la solicitud del cliente y qué versión del protocolo HTTP utilizó el servidor para responder al cliente?**

Según el encabezado el código de respuesta que indica el estado de solicitud del cliente es el siguiente HTTP/1.1 200 OK donde

- "HTTP/1.1" indica la versión del protocolo HTTP que se está utilizando
- "200" es el código de estado HTTP, que en este caso es "OK." El código "200 OK" indica que la solicitud del cliente se ha procesado correctamente, y el servidor está devolviendo una respuesta exitosa.

**Pregunta: Cualquier solicitud web determinada puede devolver una página HTML, una imagen u otros tipos de entidades. ¿Hay algo en los encabezados que crea que le dice al cliente cómo interpretar el resultado?.**

![Untitled](HTTP%20y%20URI%2099a899bef0ef4873bd1d43e4ab6b6fb9/Untitled%207.png)

Si hay algo en los encabezados que contiene información que el cliente necesita para interpretar el contenido. Por ejemplo, en el caso de encabezado "Content-Type" especifica el tipo de entidad devuelta, como HTML, imágenes o archivos de texto. Esta información permite al cliente, como un navegador web, procesar y mostrar adecuadamente el contenido. 

# **[¿Qué sucede cuando falla un HTTP request?](https://github.com/kapumota/Desarrollo-software-2023/blob/main/Semana4/Http-URI.md?classId=a1bdca4c-128c-4417-a816-076ce4107fd5&assignmentId=8d2318ef-8255-4a0a-908f-fb661c64fd86&submissionId=b5efbf24-7c8f-6a5b-d059-57d0f281874f#qu%C3%A9-sucede-cuando-falla-un-http-request)**

**Pregunta:** ¿Cuál sería el código de respuesta del servidor si intentaras buscar una URL inexistente en el sitio generador de palabras aleatorias? Pruéba esto utilizando el procedimiento anterior.