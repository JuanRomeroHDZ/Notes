---
tipo: [[Access Control List]]
tema: Ubicación de ACL
estado: Completado
region: [[Parietal]]
---
# [[ACL Placement]]
Las [[Access Control List|ACL]] por regla general se aplican donde tengan mejor rendimiento e impacto para evitar errores.
![[Pasted image 20260406144431.png]]

## [[Standard ACL Placement]]
En general, las [[Standard ACL]] se deben colocar lo más cerca al [[Destination|destino]] al cual se desea bloquear o permitir el tráfico. Ya que si, como las [[Standard ACL]] solo actúan en [[Network Layer|capa 3]] con [[IP]], si se ponen lo más cercano al [[Source|origen]], bloquearías tráfico que no solo va al [[Destination|destino]] que tú quieres bloquear.

## [[Extended ACL Placement]]
En las [[Extended ACL]] pasa lo contrario; estas deben de ir por lo general lo más cercano al [[Source|origen]] para poder filtrar por [[Protocol|protocolos]], entre otros.
![[Pasted image 20260406144508.png]]