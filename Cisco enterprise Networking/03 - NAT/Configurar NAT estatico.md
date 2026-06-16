

una configuracion NAT estatica se basa casi unicamente en dos pasos.

el primer paso consistiria en hacer la asginacion entre la direccion local interna y las direcciones globales internas.
![[Pasted image 20260412193636.png]]

despues de haber creado la asignacion de direcciones. continuacmos con el segundo paso a las asignaciones en las interfacez.
las interfaces que participan en la traduccion se configuran como interna o externa con respecto a
NAT. En el ejemplo, la interfaz R2 Serial 0/1/0 es una interfaz interna y la Serie 0/1/1 es una interfaz externa.

![[Pasted image 20260412193850.png]]


Con esta configuracion, los paquetes que llegan a la interfaz interna de R2 (Serie 0/1/0) desde la direccion IPv4 local interna configurada (192.168.10.254) se traducen y luego se reenvian hacia la red externa. Los paquetes que llegan a la interfaz externa de R2 (Serie 0/1/1), que se dirigen a la direccion IPv4 global interna configurada (209.165.201.5), se traducen a la direccion local interna (192.168.10.254) y luego se envían a dentro de la red.


Para verififcar empleamos el comando "show ip nat translations". lo cual nos mostrara algo como lo siguiente.

![[Pasted image 20260412195319.png]]


Otro comando util es show ip nat statistics, el que muestra informacion sobre el numero total de traducciones activas, los parametros de configuración de NAT, el número de direcciones en el grupo y el número de direcciones que se han asignado.

Para verificar que la traducción NAT está funcionando, es mejor borrar las estadísticas de cualquier traducción anterior utilizando el "clear ip nat statistics" comando antes de realizar la prueba.

![[Pasted image 20260412195440.png]]


![[Pasted image 20260412195516.png]]

