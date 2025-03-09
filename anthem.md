# THM - Anthem
[TryHackMe-Anthem](https://tryhackme.com/room/anthem)

Para comenzar el análisis se realiza un **nmap** a la ip de la máquina.

![Nmap](/img/anthem1.png)

*Try Hack Me*  
![THM1](/img/anthem2.png)

*Try Hack Me*  
![THM2](/img/anthem3.png)

Al acceder a la web y al archivo *robots.txt* puede verse lo que parece una contraseña y varios directorios a los que poder acceder.

![robots.txt](/img/anthem4.png)

*Try Hack Me*  
![THM3](/img/anthem5.png)

Al navegar a uno de los directorios que aparecen en el archivo puede verse el CMS llamado *umbraco*.

![umbraco](/img/anthem6.png)

*Try Hack Me*  
![THM4](/img/anthem8.png)

A continuación se va a analizar la web principal.

![web](/img/anthem9.png)

*Try Hack Me*  
![THM5](/img/anthem10.png)

En una de las publicaciones puede verse un poema.

![poema](/img/anthem11.png)

Al buscar el poema en Google viene el nombre de su autor, el cual puede ser el nombre del administrador.

*Try Hack Me*  
![THM6](/img/anthem12.png)

En otra de las publicaciones de la web, puede verse el formato que utilizan para crear los correos electrónicos.

![correo](/img/anthem13.png)

*Try Hack Me*  
![THM7](/img/anthem14.png)

Una vez obtenidos el correo y la contraseña se puede iniciar sesión en la web que se encontró anteriormente.

![umbraco](/img/anthem15.png)

Una vez en el perfil hay que navegar a través de las distintas pestañas para encontrar las flags.

![flag1](/img/anthem16.png)

*Try Hack Me*  
![THM8](/img/anthem17.png)

![flag2](/img/anthem18.png)

*Try Hack Me*  
![THM9](/img/anthem19.png)

![flag3](/img/anthem20.png)

*Try Hack Me*  
![THM10](/img/anthem21.png)

![flag4](/img/anthem22.png)

*Try Hack Me*  
![THM11](/img/anthem23.png)

A continuación se va a intentar acceder por RDP a la máquina vulnerable. Para ello se va a utilizar ***remmina***. 

![remina](/img/anthem24.png)

Una vez configurado con la ip, el usuario y la contraseña tendremos acceso a la máquina, en la que hay un txt en el escritorio con la primera flag.

![remina](/img/anthem25.png)

*Try Hack Me*  
![THM12](/img/anthem26.png)

Para obtener privilegios hay que buscar un archivo llamado *restore.txt*, el cual se encuentra oculto.

![oculto](/img/anthem27.png)

Este archivo no puede abrirse sin privilegios, por lo que hay que acceder a las propiedades del txt.

![properties](/img/anthem29.png)

Obtener el usuario actual del sistema para que tenga permisos para acceder.

![usuario](/img/anthem28.png)

Añadir al usuario en los permisos del archivo.

![remina](/img/anthem30.png)

Al acceder al archivo puede verse la contraseña del administrador.

![contraseña](/img/anthem31.png)

*Try Hack Me*  
![THM13](/img/anthem32.png)

Crear una nueva sesión RDP con privilegios de administrador.

![admin](/img/anthem33.png)

Al acceder al escritorio del administrador el archivo *root.txt* contiene la segunda flag.

![flag2](/img/anthem34.png)

*Try Hack Me*  
![THM14](/img/anthem35.png)