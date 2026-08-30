---
tipo: [[OSPF States]]
tema: Estado Two-Way OSPF
estado: Completado
region: [[Parietal]]
---
# [[Two-Way State]]
El estado `[[Two-Way State]]` es la etapa donde dos routers [[OSPF]] han establecido una comunicación bidireccional. Se alcanza cuando un router recibe un [[OSPF Hello Packet|paquete Hello]] de su vecino que contiene su propio [[Router ID]] en la lista de vecinos. Es el primer paso fundamental para formar una relación de vecindad.

## Comportamiento según el tipo de red

| Tipo de Red                | Comportamiento en Two-Way                                                             |
| :------------------------- | :------------------------------------------------------------------------------------ |
| [[Multi-access Network]]   | Crucial para la elección de [[DR]] y [[BDR]].                                         |
| [[Point-to-Point Network]] | Transición directa de [[Init State]] a [[Two-Way State]] y luego a [[ExStart State]]. |

## Implicaciones y Troubleshooting
En redes de difusión, los routers [[DROther]] permanecen en estado `2-Way` con otros [[DROther]], ya que solo forman adyacencias [[Full State|Full]] con el [[DR]] y el [[BDR]].

> Nota: Es normal que el estado sea `2-Way` entre [[DROther]], pero no debe persistir si el router debería formar una adyacencia completa con un [[DR]]/[[BDR]].

Si un router que debería ser [[DR]] o [[BDR]] permanece en `2-Way`, indica un problema de configuración (ej. prioridad [[DR]] igual a 0 en ambos extremos).