---
tipo: [[VPN]]
tema: VPN IPsec Sitio a Sitio
estado: Completado
region: [[Parietal]]
---
# [[Site-to-Site VPN|VPN IPsec Sitio a Sitio]]
Las VPN de sitio a sitio se utilizan para conectar redes a través de otra red no confiable como Internet. En una VPN de sitio a sitio, los usuarios finales envían y reciben tráfico normal de [[TCP/IP]] sin encriptar a través de un dispositivo VPN de terminación.

La terminación de VPN generalmente se denomina puerta de enlace VPN. Un dispositivo de puerta de enlace VPN podría ser un enrutador o un firewall. Por ejemplo, el Cisco Adaptive Security Appliance ([[Cisco ASA]]) es un dispositivo de firewall independiente que combina firewall, concentrador de VPN y funcionalidad de prevención de intrusiones en una imagen de software.

| Componente de Red | Rol dentro de la Arquitectura |
| :--- | :--- |
| [[Usuarios Finales]] | Envían y reciben tráfico convencional [[TCP/IP]] sin cifrar dentro de la red local local. |
| [[VPN Gateway\|Puerta de Enlace VPN]] | Dispositivo físico (como un [[Router]] o [[Firewall]]) que actúa como punto de terminación y procesamiento del túnel. |
| [[Cisco ASA]] | Hardware dedicado que unifica servicios de seguridad perimetral, concentrador de [[VPN]] y prevención de intrusiones. |

![[Pasted image 20260430140403.png]]