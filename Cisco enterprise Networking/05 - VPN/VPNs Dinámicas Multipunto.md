---
tipo: [[VPN]]
tema: VPNs Dinámicas Multipunto (DMVPN)
estado: Completado
region: [[Parietal]]
---
# [[Dynamic Multipoint VPN|VPNs Dinámicas Multipunto (DMVPN)]]
Las VPN dinámicas multipunto ([[DMVPN]]) son una solución basada en el concepto de [[GRE sobre IPsec]]. A diferencia de la arquitectura [[GRE]] convencional con [[IPsec]] estático, la tecnología multipunto es mucho más eficiente cuando se tiene una gran cantidad de sitios simultáneos a los cuales se necesita acceder.

Esta tecnología genera una topología en malla ([[Mesh Topology|mesh]]) para que los diferentes nodos remotos ([[Spoke|spokes]]) se puedan conectar al mismo tiempo a diferentes sitios o puntos de destino mediante la infraestructura de la red del túnel en malla.

| Característica | [[GRE sobre IPsec]] Convencional | [[DMVPN]] (Multipunto Dinámico) |
| :--- | :--- | :--- |
| **Topología** | Conexiones estáticas fijas de punto a punto. | Red flexible en malla ([[Mesh Topology\|mesh]]) bajo demanda. |
| **Escalabilidad** | Compleja e ineficiente al incrementar el número de sitios a la vez. | Altamente eficiente para interconectar múltiples nodos de forma simultánea. |
| **Establecimiento de Túneles** | Requiere definir manualmente cada extremo del canal. | Los [[Spoke\|spokes]] levantan túneles directos entre sí de manera dinámica. |

![[Pasted image 20260515141655.png]]
![[Pasted image 20260515141736.png]]