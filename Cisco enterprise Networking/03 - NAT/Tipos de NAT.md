---
tipo: [[Network Address Translation|NAT]]
tema: Tipos de NAT
estado: Completado
region: [[Parietal]]
---
# [[Tipos de NAT]]
Existen principalmente dos métodos para implementar la traducción de direcciones [[IPv4]] en routers [[Cisco]]:

## [[Static NAT|NAT Estática]]
La [[Static NAT|NAT estática]] se basa en asignar una dirección global interna específica a un dispositivo en concreto de manera permanente. Es una relación uno a uno.

*   **Uso:** Ideal para servidores o dispositivos finales específicos que necesitan una salida a Internet constante y una dirección que no varíe.
*   **Ventaja:** Permite acceder a recursos internos (como un servidor [[SSH]]) desde el exterior con la certeza de que la dirección [[IP]] pública asignada siempre será la misma.

![[Pasted image 20260412151854.png]]

## [[Dynamic NAT|NAT Dinámica]]
La [[Dynamic NAT|NAT dinámica]] funciona mediante un conjunto (pool) de direcciones públicas. Las direcciones se asignan a los dispositivos que desean salir a Internet bajo un esquema de "primer llegado, primer servido" (orden de llegada).

*   **Funcionamiento:** El router asigna una dirección [[IPv4]] pública siempre y cuando haya una disponible en el conjunto.
*   **Limitación:** Si el pool de direcciones está agotado, los dispositivos nuevos deben esperar hasta que una dirección se desocupe.

![[Pasted image 20260412152405.png]]