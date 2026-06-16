

Cuando los usuarios de una red deberan eviar paquetes fuera de la redes que no sean ospf como el internet, en esos casos se necesita una ruta estatica en general el router que esta en esa posicion necesita propagar su ruta estatica. el router se le suele llamar como router de borde o router de puerta de enlace. sin embargo, en la termininologia del osp , el router ubicado entre el dominio de enrutamiento ospf y una red que no es ospf como el internet en este caso. a esos se les llama router de frontera de sistema autonomo o "ASBR".

![[Pasted image 20260318193646.png]]



Todo lo que se requiere para que R2 llegue a Internet es una ruta estática predeterminada para el proveedor de servicios.

**Nota:** En este ejemplo, se utiliza una interfaz loopback con la dirección IPv4 64.100.0.1 para simular la conexión con el proveedor de servicios.

Para propagar una ruta predeterminada, el router de borde (R2) debe configurarse con lo siguiente:

- Una ruta estática predeterminada, mediante el **ip route 0.0.0.0 0.0.0.0** [_next-hop-address_ | _exit-intf_] comando.
- The **default-information originate** comando de configuración del router. Esto ordena al R2 que sea el origen de la información de la ruta predeterminada y que propague la ruta estática predeterminada en las actualizaciones OSPF.

En el ejemplo siguiente, R2 se configura con un loopback para simular una conexión a Internet. A continuación, se configura una ruta predeterminada y se propaga a todos los demás routers OSPF en el dominio de enrutamiento.

**Nota:** Al configurar rutas estáticas, se recomienda utilizar la dirección IP de salto siguiente. Sin embargo, al simular una conexión a Internet, no hay dirección IP de salto siguiente. Por lo tanto, usamos el argumento _exit-intf_

R2(config)# **interface lo1**

R2(config-if)# **ip address 64.100.0.1 255.255.255.252**

R2(config-if)# **exit**

R2(config)# **ip route 0.0.0.0 0.0.0.0 loopback 1**

%Default route without gateway, if not a point-to-point interface, may impact performance

R2(config)# **router ospf 10**

R2(config-router)# **default-information originate**

R2(config-router)# **end**

R2#




En resumen este tema es para anunciar un ruta de red diferente de la de ospf el cual se genera en la ASBR el cual anunciar la ruta para que el trafico viaje por ahi.