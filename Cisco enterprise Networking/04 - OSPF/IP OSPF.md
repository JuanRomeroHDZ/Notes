---
tipo: [[OSPF]]
tema: Configuración OSPF en Interfaz
estado: Completado
region: [[Parietal]]
---
# [[OSPF Interface Configuration]]
Para configurar [[OSPF]] directamente en las interfaces de red, se emplea el comando `ip ospf` bajo el modo de configuración de interfaz. Este método es una alternativa al comando `network` global.

## Sintaxis
La sintaxis para activar el protocolo en una interfaz específica es:
`Router(config-if)# ip ospf [process-id] area [area-id]`

| Parámetro | Descripción |
| :--- | :--- |
| `process-id` | Identificador del proceso [[OSPF]] local en el router. |
| `area-id` | Identificador del área [[OSPF]] donde pertenece la interfaz. |

> Nota: Este método habilita [[OSPF]] únicamente en la interfaz donde se aplica el comando, ignorando la necesidad de definir máscaras wildcard.

![[Pasted image 20260302225403.png]]
