# THM - Bolt
[TryHackMe-Pickle Rick](https://tryhackme.com/room/picklerick)

Para comenzar el análisis se va a realiza un **nmap** para descubrir datos como el sistema operativo o los puertos que están abiertos.

![Nmap1](/img/picklerick1.png)

![Nmap2](/img/picklerick2.png)

A continuación va a dejarse funcionando la herramienta **feroxbuster**.

![feroxbuster](/img/picklerick5.png)

Mientras la herramienta está en funcionamiento va a comenzar a analizarse la aplicación que se ha encontrado.  
Si se inspecciona el código de la página puede verse un **nombre de usuario** que puede ser útil en el futuro.

![Web](/img/picklerick3.png)

A continuación se van a buscar los típicos archivos que se pueden encontrar desprotegidos en las web como el *robots.txt* donde se ha encontrado lo que podría ser la **contraseña del usuario** que se encontró previamente.

![robots.txt](/img/picklerick4.png)

La herramienta feroxbuster ha encotrado que hay un archivo ***login.php***, en el cual puede iniciarse sesión con el usuario y contraseña que han sido encontrados previamente.

![login](/img/picklerick6.png)

Una vez se inicia sesión se ve una línea de comandos en la cual si se ejecuta un *ls*, pueden verse algunos archivos.

![comandos](/img/picklerick7.png)

Si buscamos el primer archivo que aparece, se puede ver el primer ingrediente.

![primerIngrediente](/img/picklerick8.png)

*Try Hack Me*  
![THM1](/img/picklerick13.png)

Como el sistema operativo que se ha detectado es un Linux se va a realizar un ***reverse shell*** para acceder al sistema. Este se puede encontrar en *Payloads All The Things* para *PHP*.

![comando](/img/picklerick16.png)

Modificando la ip, puede ejecutarse desde la línea de comandos de la página web, colocando previamente un netcat en escucha en el puerto que se ha seleccionado.

![netcat](/img/picklerick9.png)

Una vez ejecutado el comando desde la página web, ya tendríamos la consola preparada. Si se ejecuta *sudo -l* puede verse que para el usuario *www-data* no se necesita contraseña.

![sudo](/img/picklerick10.png)

Desde este punto ya se podrá navegar a las distintas carpetas del sistema para encontrar los otros 2 ingredientes que faltan.

![sudo](/img/picklerick12.png)

*Try Hack Me*  
![THM1](/img/picklerick14.png)

![sudo](/img/picklerick11.png)

*Try Hack Me*  
![THM1](/img/picklerick15.png)
