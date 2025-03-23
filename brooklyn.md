[TryHackMe-Brooklyn Nine Nine](https://tryhackme.com/room/brooklynninenine)

Para comenzar el análisis se realiza un **nmap** a la ip de la máquina.

![Nmap](/img/brooklyn1.png)

Como puede verse, en el puerto 21 hay un txt al cual puede accederse por ftp con el usuario y contraseña *anonymous*.

![ftp](/img/brooklyn2.png)

Una vez en la consola del ftp puede descargarse el archivo *note_to_jake.txt*.

![get](/img/brooklyn3.png)

Al ver el contenido del archivo, puede verse un mensaje en el que alertan al usuario de que su contraseña es muy débil.

![nota.txt](/img/brooklyn4.png)

Como en el escaneo de puertos se descubrió que había un puerto abierto para ssh, se va a intentar descubrir la contraseña del usuario gracias a la herramienta ***Hydra***. Una vez ejecutada la herramienta se ha encontrado la contraseña del usuario *jake* que es *987654321*. 

![hydra](/img/brooklyn5.png)

A continuación se accede por ssh gracias al usuario, la ip y la contraseña obtenida.

![ssh](/img/brooklyn6.png)

Al navegar por los directorios se encuentra el archivo *user.txt* en el que se encuentra la primera flag.

![user.txt](/img/brooklyn7.png)

*Try Hack Me*  
![THM1](/img/brooklyn8.png)

A continuación se listan los privilegios del usuario y se ve que están ligados al comando *less*.

![sudo-l](/img/brooklyn9.png)

Al ejecutar el comando *less /etc/profile*, se abre un editor en el que hay que escribir lo siguiente y pulsar intro:

![less](/img/brooklyn10.png)

De esta forma se obtiene una nueva consola con privilegios de *root*.

![whoami](/img/brooklyn11.png)

Al navegar por la carpeta de *root* se encuentra el archivo *root.txt*, en el que se encuentra la segunda flag.

![root.txt](/img/brooklyn12.png)

*Try Hack Me*  
![THM2](/img/brooklyn13.png)