
Existen dos tipos de ACL IPv4:

- ACL estándar: permiten o deniegan paquetes basándose únicamente en la dirección IPv4 de origen.
- ACL ampliadas: permiten o deniegan paquetes en función de la dirección IPv4 de origen y la dirección IPv4 de destino, el tipo de protocolo, los puertos TCP o UDP de origen y destino y más.

Por ejemplo, consulte el siguiente comando ALC estándar.

![[Pasted image 20260406143419.png]]


ACL 10 permite hosts en la red de origen 192.168.10.0/24. Debido al "negar cualquiera" implícito al final, todo el trafico, excepto el trafico que
proviene de la red 192.168.10.0/24, está bloqueado con esta ACL.

En el siguiente ejemplo, un ACL 100 extendido permite el trafico que se origina desde cualquier host en la red 192.168.10.0/24 a cualquier red
IPv4 si el puerto del host de destino es 80 (HTTP).

![[Pasted image 20260406143452.png]]



### Listas ACL nombradas y numeradas


ACLs numeradas

Las ACL número 1 a 99, o 1300 a 1999 son ACL estándar, mientras que las ACL número 100 a 199, o 2000 a 2699 son ACL extendidas, como
se muestra en la salida.

![[Pasted image 20260406143741.png]]


ACLs nombradas

Las ACL con nombre son el método preferido para configurar ACL. Específicamente, las ACL estándar y extendidas se pueden nombrar para
proporcionar informacion sobre el proposito de la ACL. Por ejemplo, nombrar un FILTRO FTP-ACL extendido es mucho mejor que tener un ACL
100 numerado.

El comando de configuración ip access-list global se utiliza para crear una ACL con nombre, como se muestra en el siguiente ejemplo.

![[Pasted image 20260406143849.png]]

