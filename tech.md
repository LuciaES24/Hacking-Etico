# THM - Tech_Supp0rt: 1
[TryHackMe-Tech_Supp0rt: 1](https://tryhackme.com/room/techsupp0rt1)

Para comenzar el análisis se realiza un **nmap** a la ip de la máquina.

![Nmap](/img/tech1.png)

![Nmap2](/img/tech2.png)

Como puede verse en el escaneo hay una vulnerabilidad en Samba.

A continuación se van a buscar los posibles directorios ocultos en el servidor web que se encuentra en dicha dirección.

![feroxbuster](/img/tech3.png)

Como puede verse en la imagen, se han encontrado 2 directorios. En el directorio *test*, pueden verse distintas alertas pero nada interesante.

![test](/img/tech4.png)

El segundo direntorio encontrado es wordpress, en el que tampoco se ha podido encontrar ningun dato relevante.

![wordpress](/img/tech5.png)

Como se ha detectado una vulnerabilidad en Samba, se va a intentar acceder a este con el comando *smbclient*. Para acceder se utiliza la contraseña *anonymous*.

![smbclient](/img/tech6.png)

Al acceder puede verse un archivo llamado *enter.txt*, en el que se pueden ver las credenciales de ***Subrion***.

![enter.txt](/img/tech7.png)

Al desencriptar la cadena encontrada en las credenciales obtenemos la contraseña del usuario *admin*.

![cyberchef](/img/tech8.png)

Al acceder al archivo robots.txt pueden verse dintintos directorios a los que se puede acceder.

![robots.txt](/img/tech9.png)

Si se accede al directorio */panel/*, puede iniciarse sesión con las credenciales que se han encontrado anteriormente.

![panel](/img/tech10.png)

Al acceder a la web y ver la versión de Subrion he buscado información sobre la misma y puede verse que existe un exploit para una vulnerabilidad de subida de archivos.

![exploit](/img/tech11.png)

Se ejecuta el exploit que se ha descargado desde la web, configurando la url, el usuario y la contraseña.

![python](/img/tech12.png)

Vemos los usuarios que se encuentran en el sistema, en el que destaca uno llamado *scamsite*, en cual tiene un nombre similar a la contraseña que encontramos anteriormente, además de que tiene los mismos permisos que el usuario *root*.

![cat1](/img/tech13.png)

![cat2](/img/tech14.png)

A continuación, tras navegar por las distintas carpetas, se ha encontrado una llamada *wordpress*.

![ls](/img/tech15.png)

En esta carpeta se encuentra el archivo *wp-config.php*, el cual tras analizar su contenido puede verse una contraseña la cual puede que coincida con la contraseña del sistema del usuario *scamsite*.

![password](/img/tech16.png)

Accedemos por ssh al sistema con el nombre de usuario, la ip y la contraseña.

![ssh](/img/tech17.png)

Vemos los permisos que tiene el usuario y me llama la atención la palabra *iconv*. Tras buscar información sobre esto, es un comando sirve para modificar la codifiación de un fichero.

![iconv](/img/tech18.png)

Tras utilizar el comando especificando la codificación en utf-8 y suponiendo que el archivo *root.txt* se encuentra en el directorio *root*, hemos encontrado la flag.

![flag](/img/tech19.png)

*Try Hack Me*  
![THM](/img/tech20.png)
