---
tipo: [[OSPF]]
tema: Fundamentos OSPF
estado: Completado
region: [[Parietal]]
---
# [[Open Shortest Path First|OSPF]]
[[OSPF]] es un protocolo de enrutamiento dinámico de [[Link-State Routing Protocol|estado de enlace]] diseñado para redes [[IP]]. Utiliza el algoritmo de Dijkstra ([[Shortest Path First|SPF]]) para determinar la ruta más rápida y eficiente basada en el costo (ancho de banda), ofreciendo una convergencia rápida y escalabilidad.

| Versión | Protocolo de Red |
| :--- | :--- |
| [[OSPFv2]] | [[IPv4]] |
| [[OSPFv3]] | [[IPv6]] |

## Comparativa: OSPF vs RIP
[[OSPF]] se desarrolló como alternativa a [[RIP]] ([[Distance Vector Routing Protocol]]). A diferencia de [[RIP]], que utiliza conteo de saltos (ineficiente en redes grandes), [[OSPF]] escala mejor y ofrece una convergencia mucho más rápida.

![[Pasted image 20260207212431.png]]

## Bases de Datos [[OSPF]]
Estas tablas se mantienen en la [[RAM]] del [[Router]]:

| Base de Datos                | Función                              |
| :--------------------------- | :----------------------------------- |
| [[Adjacency Database]]       | Crea la tabla de vecinos.            |
| [[Link State Database LSDB]] | Crea la tabla de topología completa. |
| [[Forwarding Database]]      | Crea la tabla de enrutamiento final. |

![[Pasted image 20260207212417.png]]

## Enrutamiento Jerárquico (Áreas)
El enrutamiento jerárquico mejora la eficacia y escalabilidad mediante el uso de áreas.

| Implementación       | Descripción                                                                                          |
| :------------------- | :--------------------------------------------------------------------------------------------------- |
| [[Single-Area OSPF]] | Todos los routers están en la misma área (Recomendado: [[Area 0]]).                                  |
| [[Multi-Area OSPF]]  | Implementación jerárquica. Las áreas deben conectarse al [[Backbone Area \| Área Troncal (Área 0)]]. |

> Nota: Los routers que interconectan áreas en [[Multi-Area OSPF]] se denominan [[ABR]] (Area Border Routers).

![[Pasted image 20260207214236.png]]
![[Pasted image 20260207214248.png]]