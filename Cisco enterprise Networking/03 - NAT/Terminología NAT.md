---
tipo: [[NAT]]
tema: Terminología NAT
estado: Completado
region: [[Parietal]]
---
# [[NAT Terminology]]
[[NAT]] trabaja bajo traducciones en las que la red interna está sujeta a traducción. La red externa se refiere a las otras redes.

## Perspectiva de las direcciones
Es importante recordar que la terminología de [[NAT]] siempre se aplica desde la perspectiva del dispositivo con la dirección traducida:
* **Dirección interna:** La dirección del dispositivo que [[NAT]] está traduciendo.
* **Dirección externa:** La dirección del dispositivo de destino.

Además, se usan los conceptos de *local* o *global* con relación a las direcciones:
* **Dirección local:** Cualquier dirección que aparece en la parte interna de la red.
* **Dirección global:** Cualquier dirección que aparece en la parte externa de la red.

## Tipos de direcciones IPv4 en NAT
El enrutador [[NAT]] es el punto de demarcación entre las redes internas y externas.

| Tipo de Dirección | Descripción |
| :--- | :--- |
| [[Inside Local Address]] | Dirección local interna. |
| [[Inside Global Address]] | Dirección global interna. |
| [[Outside Local Address]] | Dirección local externa. |
| [[Outside Global Address]] | Dirección global externa. |

![[Pasted image 20260411224702.png]]