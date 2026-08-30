---
tipo: [[VPN]]
tema: SSL VPNs
estado: Completado
region: [[Parietal]]
---
# [[SSL VPN|SSL VPNs]]
Cuando un cliente negocia una conexión [[SSL VPN]], en realidad se conecta utilizando [[TLS]] (Transport Layer Security). [[TLS]] es la versión más nueva de SSL y a veces se expresa como SSL/TLS; sin embargo, ambos términos a menudo se usan indistintamente. 

El protocolo SSL utiliza la infraestructura de llave pública ([[Public Key Infrastructure|PKI]]) y los [[Certificados Digitales]] para autenticar a sus pares de red.

## Comparativa de Acceso Remoto: IPsec vs SSL

| Criterio de Evaluación   | [[IPsec VPN]]                                                                       | [[SSL VPN]]                                                                                                 |
| :----------------------- | :---------------------------------------------------------------------------------- | :---------------------------------------------------------------------------------------------------------- |
| **Fortaleza Principal**  | Es la mejor opción cuando la seguridad estricta y el control son el factor crítico. | Es la mejor opción cuando el soporte y la facilidad de implementación son los problemas principales.        |
| **Autenticación**        | Mecanismos de negociación robustos y encapsulación nativa.                          | Utiliza infraestructura de llave pública ([[Public Key Infrastructure\|PKI]]) y [[Certificados Digitales]]. |
| **Acceso a Recursos**    | Ofrece acceso a prácticamente cualquier aplicación o recurso de la red.             | Ofrece acceso a prácticamente cualquier aplicación o recurso de la red.                                     |
| **Criterio de Elección** | Se basa en requisitos corporativos de seguridad y políticas de TI rígidas.          | Se basa en la necesidad de acceso ágil para los usuarios y menor carga de soporte en TI.                    |

![[Pasted image 20260430133601.png]]