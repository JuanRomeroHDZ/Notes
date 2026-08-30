---
tipo: [[OSPF]]
tema: Necesidad de un DR
estado: Completado
region: [[Parietal]]
---
# [[OSPF DR and BDR Necessity]]
Las redes [[Multi-access Network]] pueden confrontar dos retos importantes para [[OSPF]] relacionados con la saturación de los [[LSA|Link State Advertisements (LSA)]].

## Desafíos en Redes Multiacceso
1.  **Creación de múltiples adyacencias:** En redes Ethernet, interconectar muchos [[Router|routers]] genera una malla donde cada router intenta formar adyacencia con todos los demás. Esto es ineficiente y conduce a un intercambio excesivo de [[LSA]].
2.  **Saturación con LSA:** Cada vez que el [[OSPF]] se inicializa o ocurre un cambio en la topología, los routers saturan la red con [[LSA]]. Al aumentar el número de routers, el número de paquetes intercambiados aumenta dramáticamente, afectando el rendimiento de la red.

![[Pasted image 20260219235421.png]]

## Solución: DR, BDR y DROTHER
Para evitar el tráfico caótico, [[OSPF]] elige un punto central de recolección y distribución de [[LSA]].

| Rol         | Descripción                                                                                                           |
| :---------- | :-------------------------------------------------------------------------------------------------------------------- |
| [[DR]]      | (Designated Router) Punto central de recolección y distribución de [[LSA]].                                           |
| [[BDR]]     | (Backup DR) Toma el lugar del [[DR]] en caso de fallo.                                                                |
| [[DROTHER]] | Routers que no actúan como [[DR]] ni [[BDR]]; forman adyacencias [[Full State \| Full]] solo con el [[DR]] y [[BDR]]. |

El [[DR]] recibe los [[LSA]] de un router y los reenvía a los demás, evitando que cada router tenga que enviar paquetes a todos los demás vecinos, reduciendo drásticamente el tráfico.

![[Pasted image 20260220000714.png]]
![[Pasted image 20260220000810.png]]