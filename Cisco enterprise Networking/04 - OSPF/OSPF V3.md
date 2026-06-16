El OSPF v3 es la versión equivalente a OSPFv2 para intercambiar prefijos IPv6 , recuerda que en IPv6 , la dirección de red se denomina prefijo y la mascara de subred se denomina longitud de prefijo.
de manera muy similar así homologo para IPv4, OSPF v3 intercambia la información de enrutamiento para completar la tabla de enrutamiento de IPv6 con prefijos remotos.

El OSPFv2 se ejecuta sobre la capa de red IPv4, comunicándose con otros pares de IPv4 de OSPF y publicando solo rutas IPv4.

OSPFv3 tiene la misma funcionalidad de OSPFv2 , pero utiliza IPv6 como transporte de la capa de red, por lo que se comunica con pares de OSPFv3 y anuncia sus  rutas IPv6. OSPFv3 también  utiliza el algoritmo SPF como motor conjunto para determinar las mejores ritas a lo largo del dominio del enrutamiento.

OSPF v3 tiende a tener procesos diferentes de su contra parte IPv4, Los procesos empleados y las operaciones son básicamente los mismos en el protocolo de enrutamiento IPv4, pero se ejecutan de forma independiente. OSPFv2 y OSPFv3 tienen tablas de adyacencia ,tablas de topologia OSPF y tablas de enrutamiento IP independientes.

![[Pasted image 20260208151507.png]]