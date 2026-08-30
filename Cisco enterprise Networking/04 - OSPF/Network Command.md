---
tipo: [[OSPF]]
tema: OSPF Network Command
estado: Completado
region: [[Parietal]]
---
# [[OSPF Network Command]]
Un tipo de red que emplea [[OSPF]] es la red [[Point-to-Point Network|punto a punto]]. El comando `network` permite especificar qué interfaces pertenecen a una red [[OSPF]] al buscar coincidencias en sus direcciones IP. Todas las interfaces donde coincida la configuración podrán enviar y recibir paquetes [[OSPF]].

## [[OSPF Network Syntax]]
La sintaxis básica para habilitar [[OSPF]] mediante el comando global es:
`Router(config-router)# network network-address wildcard-mask area area-id`

| Componente        | Descripción                                                                           |
| :---------------- | :------------------------------------------------------------------------------------ |
| `network-address` | La dirección de red o subred donde se habilitará [[OSPF]].                            |
| `wildcard-mask`   | Máscara que determina los bits que deben coincidir (inversa de la máscara de subred). |
| `area-id`         | Identificador del [[Area ID \| área]] [[OSPF]].                                       |

> Nota: El valor de `area-id` es el identificador del área. Todos los routers que pertenezcan a la misma red [[OSPF]] deben tener asignado el mismo valor de área en las interfaces correspondientes.

## Buenas Prácticas
Se recomienda como buena práctica utilizar el [[Backbone Area|área 0]] con [[OSPFv2]]. Esto facilita que la red se modifique en el futuro al habilitar [[Multiarea OSPF|OSPF multiarea]].

## Método Alternativo
También se puede configurar [[OSPF]] directamente en la interfaz física o lógica para evitar el uso del comando `network`:
`Router(config-if)# ip ospf [process-id] area [area-id]`