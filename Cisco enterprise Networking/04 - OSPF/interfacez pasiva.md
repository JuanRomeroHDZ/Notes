
de una manera predeterminada los mensajes ospf tienden a mandarse por todas las interfaces del router pero estos mensajes solo se tienen que enviar a los routers configurados con el ospf.

![[Pasted image 20260302230641.png]]


para esta configuración de interfaces pasivas se configura el loopback,  en el cual se usa el comando " passive-interface "  para evitar la transmisión de mensajes del enrutamiento a través  de una interfaz del router . pero no dejando de anunciarse asi mismo a los demas routers ospf

![[Pasted image 20260302231020.png]]

viendo la configuracion actual con el comando " show ip protocols "

