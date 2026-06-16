

la Traduccion de la Direccion del Puerto (PAT) tambien es conocida como NAT con sobrecarga. 
como ya sabemos el funcioamiento de nat es asignar direcciones privadas a una o varias direcciones publicas la cual es la manera mas comun de configuracion de NAT en empresas y hogares.

En el caso de PAT funciona muy similar pero a la hora de asignar la direccion se basa en el tipo de peticion en base a los protocolos TCP , UDP , ICMP etc. para asginar numeros de puertos. a las direcciones de salida.
Lo cual ayuda tambien a la hora de recibir los paquetes de regreso al router y mandar los paquetes con el numero de puerto de origen. tomando en cuenta que PAT no asigna el mismo numero de puerto a una misma direccion IP.

![[Pasted image 20260412153407.png]]

Siguiente puerto disponible

En el ejemplo anterior, los numeros de puerto del cliente, 1331 y 1555, no se modificaron en el router con NAT habilitada. Esta no es una situación muy probable, porque existe una gran posibilidad de que estos números de puerto ya se hayan conectado a otras sesiones activas.

PAT intenta conservar el puerto de origen inicial. Sin embargo, si el puerto de origen original ya esta en uso, PAT asigna el primer número de puerto disponible a partir del comienzo del grupo de puertos apropiado 0-511, 512-1,023 o 1,024-65,535. Cuando no hay más puertos disponibles y hay más de una dirección externa en el conjunto de direcciones, PAT avanza a la siguiente dirección para intentar asignar el puerto de origen inicial. Este proceso continúa hasta que no haya más puertos ni direcciones IPv4 externas disponibles.


diferencias entre NAT y PAT

![[Pasted image 20260412183540.png]]


![[Pasted image 20260412183650.png]]


![[Pasted image 20260412183704.png]]
