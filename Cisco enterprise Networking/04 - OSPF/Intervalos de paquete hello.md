

el paquete hello es el encargado de averiguar si un oruter esta inactivo o no si en caso de que no este activo el router dr eliminara de sus tabals de lsdm el router inactivo por designacion el paquete hello dura 10 segudos y muere el llamdado cautro veces mas al original osea 40 segundos en este caso. tomadno eso en cuenta se pueden modificar a un estandar ed 30 segundos y 120 de muerte del paquete.


los comandos para modificar estos tiempos son los siguiente.


```
Router(config-if)# ip ospf hello-interval seconds
```



```
Router(config-if)# ip ospf dead-interval seconds
```


![[Pasted image 20260317195417.png]]