

- NAT estatico
La NAT estatica se basa en asignar direcciones globales e internas a un dispositivo en concreto. como servidores o dispositvos finales muy especificos que necesitan una salida a internet que sea constante y queno varien.

![[Pasted image 20260412151854.png]]


Este tipo de NAT es muy útil cuando se tiene que acceder a servidores o dispositivos importantes de una red desde el exterior y de esta manera tengas la certeza que no cambiara. un ejemplo seria cuando te quieres conectar por ssh a al servidor lo cual permite conectarte siempre con la misma ip


- NAT dinámica

La NAT dinámica funciona mediante un conjunto de direcciones publicas la cual se le va asignando a los dispositivos que quieran salir a internet en el orden de llegada. El NAT asigna la direccione IPv4 publica siempre y cuando haya una disponible en el conjunto de las mismas.

![[Pasted image 20260412152405.png]]