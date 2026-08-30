---
tipo: [[Access Control List]]
tema: Tipos de ACL IPv4
estado: Completado
region: [[Parietal]]
---
# [[Tipos de ACL IPv4]]
Existen dos tipos de [[Access Control List|ACL]] [[IPv4]]:
* [[Standard ACL]]: permiten o deniegan paquetes basándose únicamente en la dirección [[IPv4]] de origen.
* [[Extended ACL]]: permiten o deniegan paquetes en función de la dirección [[IPv4]] de origen y la dirección [[IPv4]] de destino, el tipo de protocolo, los puertos [[TCP]] o [[UDP]] de origen y destino y más.

Por ejemplo, consulte el siguiente comando [[Standard ACL]]:
![[Pasted image 20260406143419.png]]
[[Standard ACL|ACL]] 10 permite hosts en la red de origen 192.168.10.0/24. Debido al "negar cualquiera" implícito al final, todo el tráfico, excepto el tráfico que proviene de la red 192.168.10.0/24, está bloqueado con esta [[Access Control List|ACL]].

En el siguiente ejemplo, un [[Extended ACL|ACL 100 extendido]] permite el tráfico que se origina desde cualquier host en la red 192.168.10.0/24 a cualquier red [[IPv4]] si el puerto del host de destino es 80 ([[HTTP]]).
![[Pasted image 20260406143452.png]]

## [[Numbered ACL]] y [[Named ACL]]
### [[Numbered ACL]]
Las [[Access Control List|ACL]] número 1 a 99, o 1300 a 1999 son [[Standard ACL|ACL estándar]], mientras que las [[Access Control List|ACL]] número 100 a 199, o 2000 a 2699 son [[Extended ACL|ACL extendidas]], como se muestra en la salida.

| [[Standard ACL]] (Rango) | [[Extended ACL]] (Rango) |
| :----------------------- | :----------------------- |
| 1 a 99                   | 100 a 199                |
| 1300 a 1999              | 2000 a 2699              |

![[Pasted image 20260406143741.png]]

### [[Named ACL]]
Las [[Access Control List|ACL]] con nombre son el método preferido para configurar [[Access Control List|ACL]]. Específicamente, las [[Standard ACL|ACL estándar]] y [[Extended ACL|extendidas]] se pueden nombrar para proporcionar información sobre el propósito de la [[Access Control List|ACL]]. Por ejemplo, nombrar un FILTRO FTP-ACL [[Extended ACL|extendido]] es mucho mejor que tener un [[Access Control List|ACL]] 100 numerado.
El comando de configuración `ip access-list` global se utiliza para crear una [[Access Control List|ACL]] con nombre, como se muestra en el siguiente ejemplo.
![[Pasted image 20260406143849.png]]