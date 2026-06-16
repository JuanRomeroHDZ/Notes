
Las ACL extendidas se emplean mas que las estándar por el hecho de que son mas especificas y permiten manipular el trafico de una manera mas compleja a nivel protocolos lo cual permite una mejor gestión de la red. al grado de lograr filtrar trafico al destino con los siguiente protocolos.(IP,TCP, UDP,ICMP) lo cual esto nos da una amplia gama de posibilidades de filtro



### Sintaxis ACL extendida numerada IPv4

la sintaxis de la ACL extendida es muy similar ala de la ACL estándar, solo que la extendida cuenta con unos parámetros mas un poco mas complejos lo cual nos permite adecuarla de mejor de manera ala situación e escenario.

```
Router(config)# access-list access-list-number {deny | permit | remark text} protocol source source-wildcard [operator {port}] destination destination-wildcard [operator {port}] [established] [log]
```

en el caso de la aplicacion se emplea el mismo que en las ACL estandar.

![[Pasted image 20260408185559.png]]
![[Pasted image 20260408185628.png]]
![[Pasted image 20260408185713.png]]


### protocolos y puertos

La ACL extendidas pueden filtrar muchos protoclos y puertos de inter. lo que permite conjugarlos de manera optima para la red. asi como se muestra de la siguiente manera.

![[Pasted image 20260408185858.png]]

En el caso de los puertos se hace de la siguiene manera.


![[Pasted image 20260408185950.png]]

![[Pasted image 20260408190002.png]]

esto te permite filtrar por puerto lo cual hace mas especifico el filtramiento . per cabe recalcar que en los protocolos udp, tcp, icmp. ofrecen opciones especificas de puertos relacionadas con esos protocolos.


### tcp establecido en ACL

En la TCP establecida ACL extendida funje la funcion de de servicios basicos de firewall lo cual permite filtrar trafico de salida para tener una respuesta solo de las redes o direcciones permitidas y niega al mismo tiempo los host externos.
![[Pasted image 20260408191738.png]]

la palabra clave para esto es **establised** 

![[Pasted image 20260408191848.png]]


en el siguiente ejemlo la ACL 120 esta previamente configurado para permitir solo devolver el trafico web a los host de lan. esta acl se aplica en el g0/0/0 en saliente.



![[Pasted image 20260408192007.png]]


Observe que el permiso de contadores HTTPS seguros (es decir, eq 443) en ACL 110 y los contadores de retorno establecidos en ACL 120 han
aumentado.

El parametro established established permite que solo las respuestas al trafico procedente de la red 192.168.10.0/24 vuelvan a esa red.
Específicamente, se produce una coincidencia si el segmento TCP devuelto tiene los bits de indicador ACK o reset (RST) establecidos. Esto
indica que el paquete pertenece a una conexión existente. Sin el parámetro established en la declaración de ACL, los clientes podrian enviar
tráfico a un servidor web, pero no recibir el tráfico que regresa del servidor web.
### ejemplos de configuración numerada.

![[Pasted image 20260408191044.png]]



![[Pasted image 20260408191237.png]]




### Sintaxis de ACL extendida nombrada



```
Router(config)# ip access-list extended access-list-name
```


R1(config)# **ip access-list extended NO-FTP-ACCESS**


#### ejemplo ACL extendida nombrada

Las ACL extendidas con se crean esencialmente de la misma forma que las ACL estandar con nombre.

La topología de la figura se utiliza para demostrar la configuracion y aplicacion de dos ACL IPv4 extendidas con nombre a una interfaz:

· SURFING - Esto permitirá que dentro del tráfico HTTP y HTTPS salga a Internet.
. BROWSING - Esto solo permitira devolver trafico web a los hosts internos mientras que todo el resto del trafico que sale de la interfaz
G0/0/0 en R1 está implícitamente denegado.

![[Pasted image 20260408192430.png]]


El ejemplo muestra la configuracion de la ACL de SURFING entrante y la ACL de BROWSING saliente.

La ACL de SURFING permite que el trafico HTTP y HTTPS de los usuarios internos salga de la interfaz G0/0/1 conectada a Internet. La ACL de
BROWSING permite que el tráfico web que regrese de Internet vuelva a la red privada interna.

La ACL de SURFING se aplica de entrada y la ACL de BROWSING se aplica de salida en la interfaz G0/0/0 en R1, como se muestra en el
ejemplo.

Los hosts internos han estado accediendo a los recursos web seguros desde Internet. El comando The show access-lists se utiliza para
verificar las estadísticas de ACL. Observe que los contadores HTTPS seguros de permiso (es decir, eq 443) en la ACL de SURFING y los
contadores de retorno establecidos en la ACL de BROWSING han aumentado.


![[Pasted image 20260408192559.png]]


### Editar ACL extendidas

en este caso es muy similar a las acl estándar lo cual nos permite editar las ACL de manera con editor de texto o la segunda opción que seria por números de secuencia.

![[Pasted image 20260408192921.png]]

en este caso podemos ver las ACLs en la cual en este caso nos enfocaremos en la ACL surfing, ya que en su ACE numero 10 tiene la dirección ip incorrecta ya que le falta un numero.
la manera para editarla seria de la siguiente forma.

![[Pasted image 20260408193353.png]]

vemos que primero entramos a la ACL después negamos la ACE 10 y la rescribimos con la nueva que incluye la ip correcta.

usamos el comando show access-list para verificar

![[Pasted image 20260408193520.png]]


### Ejemplo de ACL extendida nombrada.

La figura muestra otro escenario para implementar una ACL IPv4 extendida con nombre. Suponga que PC1 en la red privada interna está permitido trafico FTP, SSH, Telnet, DNS, HTTP y HTTPS. Sin embargo, se debe denegar el acceso a todos los demás usuarios de la red privada interna.

Se crearán dos ACL extendidas con nombre:

- PERMIT-PC1 - Esto sólo permitirá el acceso TCP PC1 a Internet y denegara todos los demás hosts de la red privada.
- REPLY-PC1 - Esto sólo permitirá que el tráfico TCP devuelto especificado a PC1 deniegue implícitamente todo el resto del tráfico.


![[Pasted image 20260408194630.png]]

La PERMIT-PC1 ACL permite el acceso TCP PC1 (es decir, 192.168.10.10) al tráfico FTP (es decir, puertos 20 y 21), SSH (22), Telnet (23), DNS (53), HTTP (80) y HTTPS (443). La REPLY-PC1 ACL permitirá el tráfico de retorno a PC1.

Hay muchos factores a tener en cuenta al aplicar una ACL, entre los que se incluyen:

· El dispositivo para aplicarlo
· La interfaz para aplicarlo
· La dirección para aplicarlo

Se debe tener en cuenta cuidadosamente para evitar resultados de filtrado no deseados. La ACL PERMIT-PC1 se aplica entrante y la ACL REPLY-PC1 se aplica saliente en la interfaz R1 G0/0/0.

![[Pasted image 20260408200758.png]]


