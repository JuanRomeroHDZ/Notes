
El NAT dinámico consiste en la misma funcion o una funcion similar al DHCP ya que su mision es proporcionar direcciones o direcciones traducidad para que los dispositivos en la red peudan acceder a la red externa o internet. 
En si funciona con una pool de direcciones al igual que el DHCP y de esa manera las sigue entregando. y cuando no hay disponibles para otro dispositivo se tieen que espera hasta que una se desocupe.


### Configurar NAT dinámica

como tal la ip nat es sencilla de configurar con el siguiente listado de pasos a continuación

- 1

![[Pasted image 20260428210042.png]]

- 2

![[Pasted image 20260428210108.png]]


- 3


![[Pasted image 20260428210124.png]]


- 4


![[Pasted image 20260428210135.png]]

- 5

![[Pasted image 20260428210150.png]]




### Analizar NAT dinamico

#### Interio a exterior


![[Pasted image 20260428210837.png]]

![[Pasted image 20260428210901.png]]


#### Exterior a Interio

![[Pasted image 20260428211532.png]]

![[Pasted image 20260428211600.png]]



### Verificar NAT dinamica

para ver la salida de de las traducciones empleamos el comando " show ip nat translations "
la cual nos mostrara las traducciones estaticas que se han configurado.

![[Pasted image 20260428212510.png]]

![[Pasted image 20260428212539.png]]


![[Pasted image 20260428212706.png]]


![[Pasted image 20260428212732.png]]

![[Pasted image 20260428212750.png]]

![[Pasted image 20260428213008.png]]

