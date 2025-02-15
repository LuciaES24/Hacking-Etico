# THM - Bolt
[TryHackMe-Bolt](https://tryhackme.com/room/bolt)

Para comenzar el análisis se realiza un **nmap** a la ip de la máquina para descubrir datos como el sistema operativo o los puertos que están abiertos.

![Nmap1](/img/bolt1.png)

![Nmap2](/img/bolt2.png)

Como puede verse en la imagen se han detectado **3 puertos abiertos** en la máquina, entre los cuales uno de ellos en un PHP (8000), lo que significa que hay una aplicación.
Además, en el escaneo parece que no ha podido encontrarse en sistema operativo exacto de la máquina. 

*Try Hack Me*  
![THM1](/img/bolt14.png)

A continuación se va a realizar **fuzzing** a la máquina para encontrar las respuestas válidas en el sistema y los errores. Para ello se utiliza la herramienta **feroxbuster**.

![feroxbuster](/img/bolt3.png)

Mientras se ejecuta la herramienta se puede acceder a la aplicación que fue descubierta en el puerto 8000.

![aplicación](/img/bolt4.png)

Una vez en la aplicación hay que investigarla hasta ver si es posible encontrar algo de información útil.  
Desde la pantalla *Home*, puede verse un comunicado del admin publicando el **nombre del usuario** administrador.

![usuario](/img/bolt6.png)

*Try Hack Me*  
![THM2](/img/bolt15.png)

Otro mensaje que puede verse en esta pantalla contiene la **contraseña del usuario** administrador, 2 datos que pueden ser útiles próximamente.

![contraseña](/img/bolt5.png)

*Try Hack Me*  
![THM3](/img/bolt16.png)

Si se accede a la página */bolt/login*, se podrán utilizar las credenciales que han sido obtenidas.

![login](/img/bolt7.png)

Una vez dentro del perfil del administrados en la parte inferiosr izquierda de la pantalla puede verse la versión del CMS.

![versión cms](/img/bolt8.png)

*Try Hack Me*  
![THM4](/img/bolt17.png)

Una vez finalizado el análisis con *feroxbuster* no se han encotrado datos relevantes para la investigación.

Para encontrar el EDB-ID se busca la versión del CMS para ver si tiene algún exploit.

![EDB-ID](/img/bolt21.png)

*Try Hack Me*  
![THM5](/img/bolt18.png)

El siguiente paso será utilizar la herramienta **Metasploit**, concretamente ***msfconsole*** para conocer los exploits de la versión del CMS que ha sido detectada. Una vez dentro de la terminal utilizar el comando *search bolt*.

![exploit](/img/bolt9.png)

*Try Hack Me*  
![THM6](/img/bolt19.png)

Una vez encontrado el exploit que coincide con la versión, se selecciona y se ven las opciones que hay que configurar del mismo con los comandos que pueden verse en la imagen.

![useexploit](/img/bolt10.png)

A continuación hay que configurar las opciones que son obligatorias como puede verse a continuación:

![confexploit](/img/bolt11.png)

Una vez hecho esto puede ejecutarse el exploit con el comando *run*. Si todo ha ido bien podrá utilizarse la terminal para ver los archivos de la máquina vulnerable.

![terminal](/img/bolt12.png)

Una vez en la terminal puede accederse al resto de directorios, pudiendo a acceder a múltiples archivos.

![flag](/img/bolt13.png)

*Try Hack Me*  
![THM7](/img/bolt20.png)