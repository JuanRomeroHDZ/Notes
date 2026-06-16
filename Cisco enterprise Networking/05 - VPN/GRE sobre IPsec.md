
EL protocolo GRE (Generic Routing Encapsulation) es un protocolo de tunel de VPN que nos permite crear una conexion de sitio a sitio relativamente basica pero no es seguro, lo que hace como tal este protcolo es encapasular 
varios protocolos de la capa de red . tambien es compatible con el trafico multicast y broadcast lo que puede ser de gran utilidad para las empresas que requieren esos protocolos de enrutamiento lo cual les permite trabajar desde una VPN , pero lo que acotece con GRE es que no contiene ninguna capa de encriptacion por defecto y ahi es donde entra IPsec.

Las VPN con IPsec unicamente pueden crear tuneles con trafico uniscast pero no permiten por lo tanto los protocolos de enrutamiendo no intercambias informacion de enrutamiento a traves de una VPN IPsec.(multicast y broadcast)


entonces la solucion fue encapsular un GREcon todos los protocolosd e enrutamiento y de esa manera se encapsula ese paquete en uno nuevo con IPsec lo que permite mandarlo de forma seguyra a travez de la VPN IPsec.


![[Pasted image 20260515140549.png]]


![[Pasted image 20260515140705.png]]