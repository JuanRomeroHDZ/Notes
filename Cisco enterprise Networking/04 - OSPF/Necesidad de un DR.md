
Las redes multiaccceso pueden crear o confrontar dos re5tos para el OSPF en la relacion con la saturacion de los LSA.

#### Creacion de varias adyacencias:

las redes ethernet podrían interconectar con muchísimos routers OSPF conun enlace completamente común . la creacion de las adyacencias en cada router es innecesaria y no se recomienda , conduciría al intercambio excesivo de LSA entre los routers de la red.


![[Pasted image 20260219235421.png]]


#### - Saturacion con el paquete LSA:

los routers de estado de enlace saturan la conexión con sus LSA cada vez que el OSPF se inicializa cada vez que se hace un cambio en la topologia , esta saturacion puede llegar a ser excesiva.

#### Inundación de LSA con DR


cuando hay un aumento en cuanto al numero de routers de la red, también se aumenta dramáticamente el numero de paquetes LSA intercambiado entre los routers. Esta inundación de LSA afecta drasticamente al funcionamiento de OSPF.

#### Solución para Adyacencias y LSA

La solución para la cantidad excesiva de adyacencias y paquetes LSA los cuales generan un trafico caótico en la red. se basa en DR el cual el OSPF lo elije como punto de recolección y distribución de las LSA recibidas y enviadas. pero también se elije el BDR en caso de fallo del DR. y los demás routers pasan a un modo llamado DROTHER(un router que no funciona como DR o BDR) 

basicamente el DR recibe el LSA de un router y lo manda a los demas asi evitanto que todos se lo manden entre todos, lo cual genera mucho trafico.

![[Pasted image 20260220000714.png]]



![[Pasted image 20260220000810.png]]