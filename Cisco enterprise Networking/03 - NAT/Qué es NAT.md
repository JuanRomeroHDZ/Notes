---
tipo: [[Network Address Translation]]
tema: ¿Qué es NAT?
estado: Completado
region: [[Parietal]]
---
# [[Network Address Translation|NAT]]
[[NAT]] es la solución directa al agotamiento de las direcciones [[IPv4]] para acceder a [[Internet]], ya que las [[IPv4]] tienen un límite de 4 mil millones de direcciones [[IP]] (lo cual parecía mucho hace tiempo) y ahora es casi insuficiente. Así, [[NAT]] cumple el propósito de conectarnos a [[Internet]] y ahorrar [[IPv4]] al mismo tiempo.
![[Pasted image 20260411221501.png]]
[[NAT]] tiene muchos usos, pero el principal es conservar las [[Public IPv4 Address|direcciones IPv4 públicas]]. Esto se logra al permitir que las redes utilicen [[Private IPv4 Address|direcciones IPv4 privadas]] internamente y al proporcionar la traducción a una dirección pública solo cuando sea necesario. [[NAT]] tiene el beneficio percibido de agregar un grado de privacidad y seguridad a una red, ya que oculta las [[Private IPv4 Address|direcciones IPv4 internas]] de redes externas.

## Funcionamiento
Los [[Router|routers]] con [[NAT]] habilitada se pueden configurar con una o más direcciones [[IPv4]] públicas válidas. Estas direcciones públicas se conocen como [[NAT Pool|conjunto de NAT]]. Cuando un dispositivo interno envía tráfico fuera de la red, el [[Router]] con [[NAT]] habilitada traduce la [[Private IPv4 Address|dirección IPv4 interna]] del dispositivo a una dirección pública del [[NAT Pool|conjunto de NAT]]. Para los dispositivos externos, todo el tráfico entrante y saliente de la red parece tener una [[Public IPv4 Address|dirección IPv4 pública]] del conjunto de direcciones proporcionado.
En general, los [[Router|routers NAT]] funcionan en la frontera de una red de rutas internas. Una [[Stub Network|red de código auxiliar]] es una o más redes con una única conexión a su red vecina, una entrada y una salida de la red. En el ejemplo de la ilustración, el R2 es un [[Border Router|router de frontera]]. Visto desde el [[ISP]], el R2 forma una red de rutas internas.