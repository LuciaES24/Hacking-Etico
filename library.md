# THM - Library
[TryHackMe-Library](https://tryhackme.com/room/bsidesgtlibrary)

Para comenzar el análisis se realiza un **nmap** a la ip de la máquina.

![Nmap](/img/library1.png)

Como puede verse en el nmap se encuentra abierto el puerto 22 en el que hay una conexión ssh y el 80, donde hay una página web.

Al acceder a la web puede verse un nombre de usuario, el cual puede servir en un futuro.

![Web](/img/library2.png)

En la primera imagen, también puede verse que en el puerto 80 existe un archivo llamado robots.txt, al cual si se accede puede verse que quizás la contraseña del usuario que se ha encontrado previamente se encuentra en el rockyou.txt.

![robots.txt](/img/library3.png)

Como tenemos un usuario y una contraseña hay que intentar acceder por ssh. Para ello se va a utilizar ***Metasploit***, con el comando *msfconsole* y se debe buscar *ssh_login*.

![ssh_login](/img/library4.png)

A continuación hay que configurar las opciones del exploit.

```
use 0
set pass_file /home/kali/Downloads/rockyou.txt
set username meliodas
set rhosts (ip THM)
run
```

Al hacer el ataque puede verse que se ha obtenido la contraseña del usuario.

![contraseña](/img/library5.png)

Realizar la conexión por ssh, utilizando el usuario, la ip de THM y la contraseña encontrada.

![ssh](/img/library6.png)

En la carpeta del usuario puede verse el archivo *user.txt*.

![user.txt](/img/library7.png)

*Try Hack Me*  
![THM1](/img/library8.png)

Al ejecutar el comando *sudo -l* puede verse que para tener permisos hay que ejecutar con python el archivo *bak.py*. 

![sudo -l](/img/library9.png)

Sin embargo, al ejecutarlo se necesita una contraseña, por lo que hay que modificar el contenido de dicho archivo. Para ello hay que ejecutar los siguientes comandos:

```
rm bak.py 
touch bak.py
echo 'pty; pty.spawn("/bin/bash")' > bak.py
sudo python /home/meliodas/bak.py
```

Una vez ejecutado el script de python, tendremos privilegios de root. Al acceder a la carpeta *root* puede verse un archivo llamado *root.txt*.

![root](/img/library10.png)

*Try Hack Me*  
![THM2](/img/library11.png)
