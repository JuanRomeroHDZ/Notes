---
tipo: [[Protocolo de enrutamiento]]
tema: OSPFv3
estado: Completado
region: Parietal
---
# [[OSPFv3]]
[[OSPFv3]] es la versión del protocolo [[OSPF]] diseñada para el intercambio de [[Prefijo IPv6|prefijos IPv6]]. Su funcionamiento es equivalente al de [[OSPFv2]], permitiendo completar la [[Tabla de enrutamiento]] mediante la publicación de prefijos remotos.

## Funcionamiento y transporte
A diferencia de [[OSPFv2]], que se ejecuta sobre la [[Capa de red]] [[IPv4]] para anunciar rutas de dicho protocolo, [[OSPFv3]] utiliza [[IPv6]] como transporte de la [[Capa de red]]. A pesar de este cambio, ambos mantienen el uso del [[Algoritmo SPF]] para determinar las mejores rutas dentro del [[Dominio de enrutamiento]].

## Independencia operativa
Aunque [[OSPFv3]] y [[OSPFv2]] comparten la lógica de funcionamiento, operan de forma independiente. Cada protocolo mantiene sus propias estructuras de datos:
* [[Tabla de adyacencia]]
* [[Tabla de topología]]
* [[Tabla de enrutamiento]]

![[Pasted image 20260208151507.png]]