[TryHackMe-Easy Peasy](https://tryhackme.com/room/easypeasyctf)

Para comenzar el análisis se realiza un **nmap** a la ip de la máquina.

![Nmap](/img/easy1.png)

*Try Hack Me*  
![THM1](/img/easy2.png)

*Try Hack Me*  
![THM2](/img/easy3.png)

*Try Hack Me*  
![THM3](/img/easy4.png)

Se lanza la herramienta ***Feroxbuster*** para descubrir los directorios ocultos.

![feroxbuster1](/img/easy5.png)

Se accede al directorio encontrado llamado */hidden* pero no se ha encontrado nada interesante.

![hidden](/img/easy6.png)

Se buscan los directorios ocultos del nuevo directorio encontrado.

![feroxbuster2](/img/easy7.png)

Se accede al nuevo directorio llamado */whatever*.

![whatever](/img/easy8.png)

En este, al analizar el código fuente se puede encontrar una cadena codificada en base 64.

![base](/img/easy9.png)

Al descodificar la cadena se obtiene la flag.

![base64](/img/easy10.png)

*Try Hack Me*  
![THM4](/img/easy37.png)

A continuación se va a buscar información en el archivo *robots.txt* encontrado en el nmap en el puerto 65524. En este se encuentra el md5 de una cadena.

![robots.txt](/img/easy11.png)

Al desencriptar este hash se encuentra la segunda flag.

![md5](/img/easy12.png)

*Try Hack Me*  
![THM5](/img/easy13.png)

Al analizar la página que se encuentra en dicho puerto, puede verse la tercera flag.

![flag3](/img/easy14.png)

*Try Hack Me*  
![THM6](/img/easy15.png)

Al analizar el código fuente puede verse otra cadena, en este caso codificada en base 62. 

![fuente](/img/easy16.png)

Una vez desencriptada la cadena se obtiene el directorio oculto.

![base62](/img/easy17.png)

*Try Hack Me*  
![THM7](/img/easy18.png)

Al acceder a este directorio, se ve otra cadena codificada.

![directorioOculto](/img/easy19.png)

Para encontrar la contraseña se va a utilizar la herramienta ***John the ripper*** y con ayuda del archivo adjunto al ejercicio se va a obtener el resultado.

![contraseña](/img/easy20.png)

*Try Hack Me*  
![THM8](/img/easy21.png)

En el código fuente de la misma página que se acaba de analizar, se puede ver que hay una imagen que podría ser útil.

![imagen](/img/easy22.png)

Se descarga la imagen de la web con el comando *wget*.

![wget](/img/easy23.png)

Con la herramienta ***Steghide*** se extrae el archivo *.txt* enlazado a la imagen.

![steghide](/img/easy24.png)

Al ver el contenido del archivo puede verse un usuario y una contraseña escriita en binario.

![secrettext.txt](/img/easy25.png)

Al desencriptar este código se obtiene la contraseña.

![contraseña](/img/easy26.png)

*Try Hack Me*  
![THM9](/img/easy38.png)

A continuación se accede por ssh al sistema gracias al usuario obtenido, la ip y la contraseña.

![ssh](/img/easy27.png)

Puede verse un archivo llamado *user.txt* en el que se encuentra la flag del usuario pero se encuentra encriptada en ROT13.

![user.txt](/img/easy28.png)

Al desencriptarla se obtiene la flag.

![rot13](/img/easy29.png)

*Try Hack Me*  
![THM9](/img/easy30.png)

Como el usuario no tiene permisos *sudo* se accede al archivo */etc/crontab*, donde puede verse un archivo llamado *.mysecretcronjob.sh* el cual tiene permisos de *root*.

![crontab](/img/easy31.png)

Para hacer una shell reversa se comienza poniendo un puerto en escucha en el equipo.

![netcat](/img/easy32.png)

A continuación, en la línea de comandos de la máquina en la que se van a escalar privilegios se ejecuta el siguiente comando:

![comando](/img/easy33.png)

Al cabo de unos segundos se obtiene la línea de comandos con permisos de*root*.

![reverseShell](/img/easy34.png)

Se obtiene la flag del archivo *root.txt*.

![user.txt](/img/easy35.png)

*Try Hack Me*  
![THM10](/img/easy36.png)