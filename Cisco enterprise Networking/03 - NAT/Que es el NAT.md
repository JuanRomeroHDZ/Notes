
El NAT es la solucion directa al agotamiento de las direcciones ipv4 para acceder a internet ya que las ipv4 que tiene un limite de 4 mil millones de direcciones ip lo cual parecia mucho hace tiempo, ahora es casi insuficiente, asi que nat comprender y cumple el proposito de conectarnos a internet y ahorrar ipv4 al mismo tiempo.

![[Pasted image 20260411221501.png]]


NAT tiene muchos usos, pero el principal es conservar las direcciones IPv4 publicas. Esto se logra al permitir que las redes utilicen direcciones IPv4 privadas internamente y al proporcionar la traducción a una dirección pública solo cuando sea necesario. NAT tiene el beneficio percibido
de agregar un grado de privacidad y seguridad a una red, ya que oculta las direcciones IPv4 internas de redes externas.

Los routers con NAT habilitada se pueden configurar con una o más direcciones IPv4 públicas válidas. Estas direcciones públicas se conocen como "conjunto de NAT". Cuando un dispositivo interno envía trafico fuera de la red, el router con NAT habilitada traduce la direccion IPv4
interna del dispositivo a una dirección pública del conjunto de NAT. Para los dispositivos externos, todo el tráfico entrante y saliente de la red parece tener una direccion IPv4 publica del conjunto de direcciones proporcionado.

En general, los routers NAT funcionan en la frontera de una red de rutas internas. Una red de código auxiliar es una o más redes con una única conexión a su red vecina, una entrada y una salida de la red. En el ejemplo de la ilustración, el R2 es un router de frontera. Visto desde el ISP,
el R2 forma una red de rutas internas.