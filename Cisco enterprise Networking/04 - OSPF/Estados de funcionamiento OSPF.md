
incialmente los roouters nuevos en una red de OSPF hace lo siguiente en lo que consigue crear una su convergencia con los demas routers en la red.

![[Pasted image 20260219200937.png]]


### Establecimientos de Adyacencias:


cuando el ospf esta habilitado en una interfaz de router, el router debe determinar o averiguar si existe otro vecino con ospf disponible para la adyacencia, de tal manera que reenvía paquetes del tipo Hello con su ID de router por todas las interfaces que permitan o estén configuradas con ospf, de tal manera que lo mandara por la direccion multicast reservada con la ip v4 "224.0.0.5" de tal manera que solo routers con OSPF v2 lograran procesar esos paquetes, iniciando con tomar el id del paquete hello y y de ahi lograr un adyacencia.

#### Estado Down a estado init.

cuando el OSPFv2 esta habilitado en la interfaz de Gigabit por ejemplo pasa del estado down al estado init dando a entender que esta encendido, El R1 comienza a enviar paquetes de hello por todas las interfaces con OSPF para descubrir los vecinos y hacer adyacencias.

![[Pasted image 20260219232006.png]]


#### Estado init

El R2 recibe el paquete hello de R1 y agrega el router id de R1 a su lista de vecinos OSPF , después el R2 envía un paquete hello a R1 conteniendo su router id  y el router id  en la lista de vecinos de la misma interfaz de red.

![[Pasted image 20260219232338.png]]


#### Estado Two-way

R1 recibe el paquete hello y agrega el router id de R2 a si lista de vecinos OSPF , cuando el router recibe un paquete hello en el que se indica su router id en la lista de vecinos, el router pasa del estado init al estado [[Estado two way]]

La acción que se realiza en el estado two-way depende mucho de la interconexion de los routers adyacente.

![[Pasted image 20260219232754.png]]

#### Elección DR y  BDR

![[Pasted image 20260219232853.png]]