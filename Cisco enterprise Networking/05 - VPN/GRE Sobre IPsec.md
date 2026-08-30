---
tipo: [[VPN]]
tema: GRE sobre IPsec
estado: Completado
region: [[Parietal]]
---
# [[GRE over IPsec|GRE sobre IPsec]]
El protocolo `[[GRE]]` (Generic Routing Encapsulation) es un protocolo de túnel de [[VPN]] que permite crear una conexión de sitio a sitio relativamente básica. Su función principal es encapsular varios protocolos de la capa de red. 

## El Desafío de Protocolos Individuales

| Característica | [[GRE]] (Generic Routing Encapsulation) | [[IPsec]] (Internet Protocol Security) |
| :--- | :--- | :--- |
| **Soporte de Tráfico** | Admite tráfico [[Multicast]], [[Broadcast]] y [[Unicast]]. | Soporta únicamente tráfico [[Unicast]]. |
| **Protocolos de Enrutamiento** | Permite el intercambio de tablas y actualizaciones de enrutamiento. | Bloquea el intercambio de información de enrutamiento dinámico debido a la falta de multicast. |
| **Seguridad y Cifrado** | No contiene ninguna capa de cifrado o encriptación por defecto. | Proporciona una suite completa de seguridad y cifrado fuerte de datos. |

## La Solución: GRE sobre IPsec
Dado que `[[GRE]]` aporta la flexibilidad de transporte y `[[IPsec]]` aporta la seguridad, la solución de ingeniería consiste en unificar ambos métodos:

1. El tráfico de la red local junto con los protocolos de enrutamiento se encapsulan primero dentro de un paquete `[[GRE]]` (lo que permite procesar el tráfico [[Multicast]] y [[Broadcast]]).
2. Posteriormente, ese paquete resultante se encapsula dentro de un nuevo paquete protegido por `[[IPsec]]`.

De esta manera, la información viaja de forma completamente segura a través de la [[VPN]] pública sin perder las capacidades de enrutamiento dinámico entre los sitios.

![[Pasted image 20260515140549.png]]
![[Pasted image 20260515140705.png]]