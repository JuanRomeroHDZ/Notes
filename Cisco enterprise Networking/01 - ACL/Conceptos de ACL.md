---
tipo: [[Access Control List]]
tema: Conceptos de ACL
estado: Completado
region: [[Parietal]]
---
# [[Access Control List]]
Los enrutadores son los que toman las decisiones de enrutamiento basadas en la información del encabezado del paquete. Así el tráfico que entra a una interfaz de enrutador se enruta únicamente en función de la información dentro de la tabla de enrutamiento. El router compara la dirección [[IP]] de destino con las rutas de la tabla de enrutamiento para encontrar la mejor coincidencia y, a continuación, reenvía el paquete según la mejor ruta de coincidencia. Exactamente ese mismo proceso se puede utilizar para filtrar el tráfico mediante una [[Access Control List|ACL]]. Las [[Access Control List|ACL]] funcionan filtrando paquetes en las capas 3 ([[Network Layer]]) y 4 ([[Transport Layer]]) del [[Modelo OSI]].
## Ejemplos de tareas
![[Pasted image 20260406122252.png]]
![[Pasted image 20260406122545.png]]
## Tipos de ACL
Los [[Router|routers]] [[Cisco]] admiten dos tipos de ACL. Aunque existen varios tipos de ACL incluso para [[VLAN]] directamente en los [[Switches de capa 3]], en los routers [[Cisco]] se admiten las siguientes:
### [[Standard ACL]]
Las [[Standard ACL]] solo filtran en la capa 3 utilizando únicamente la dirección [[IPv4]] de origen.
### [[Extended ACL]]
Las [[Extended ACL]] filtran en la capa 3 mediante la dirección [[IPv4]] de origen o destino; también puede filtrar en la capa 4 mediante [[TCP]], puertos [[UDP]] e información de tipo de protocolo opcional para un control más exacto en las redes.
## [[Numbered ACL]] y [[Named ACL]]
Las [[Numbered ACL|ACL numeradas]] y [[Named ACL|nombradas]] como tal no son dos ACLs nuevas, sino que son dos términos al crear una ACL ya que puedes crear una [[Standard ACL]] o [[Extended ACL]] con un número ([[Numbered ACL|ACL numerada]]) en vez de un nombre (por ejemplo: "ACL 10, 20 o 30"), y a su vez puedes crear una ACL con un nombre en específico ([[Named ACL|ACL nombrada]]) por ejemplo: "Bloquear youtube" y de esa manera no pones un número como las numeradas.
![[Pasted image 20260406124254.png]]