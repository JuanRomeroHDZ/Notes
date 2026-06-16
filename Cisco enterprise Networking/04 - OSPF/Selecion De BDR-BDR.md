
para la elección del Router DR y BDR se basa en algunos criterios los cuales son los siguiente:

* Prioridad de interfaz mas alta
para la elección de Router DR y el de respaldo BDR se usa el la prioridad de interfaz mas alta y la segunda mas alta para el BDR, sin embargo si no hay prioridad se optara por el router-id.
* Router-id mas alto
El Router id configurado mas alto será el Router DR designado y la segunda mas alta el BDR, al igual que el anterior si no hay una configurada se optara por el Loopback
* loopback mas alto
Es similar a las antreriores aqui la direccion IPv4 configurada en loopback sera el DR y la segunda mas alta el BDR o si tampoco hay ninguna configurada se optara por la direccion ip.
* dirección IPv4 mas alta
Como ultimo recurso de si no hay interfaces configuradas en el loopback el router id lo determinara la direccion IPv4 mas alta activa.
![[Pasted image 20260309212326.png]]



#### Configurar prioridad

para configurar la prioridad en la eleccion del router DR y BDR se puede configurar la prioridad con el comando "ip ospf priority" directamente en la interfaz, como en la siguiente imagen:

![[Pasted image 20260309213048.png]]

para borrar la configuraciond e OSPF se emplea el comando "clear ip ospf process"  en el modo privilegiado.

![[Pasted image 20260309213148.png]]


![[Pasted image 20260309213220.png]]