---
tipo: [[OSPF]]
tema: Selección de BDR
estado: Completado
region: [[Parietal]]
---
# [[DR and BDR Selection]]
La elección de los routers [[DR]] (Router Designado) y [[BDR]] (Router Designado de Respaldo) se basa en una serie de criterios secuenciales de mayor a menor preferencia.

| Criterio de Selección | Mecanismo de Evaluación |
| :--- | :--- |
| **1. Prioridad de interfaz más alta** | Se utiliza la prioridad de interfaz más alta para elegir al [[DR]] y la segunda más alta para el [[BDR]]. Si las prioridades son iguales, se evalúa el [[Router ID]]. |
| **2. Router ID más alto** | El [[Router ID]] configurado explícitamente más alto será el [[DR]] y el segundo más alto será el [[BDR]]. Si no hay uno configurado, se evalúa la loopback. |
| **3. Loopback más alta** | La dirección [[IPv4]] activa más alta configurada en una [[Loopback Interface\|interfaz loopback]] será el [[DR]] y la segunda más alta el [[BDR]]. Si tampoco existen, se evalúa la dirección física. |
| **4. Dirección IPv4 física más alta** | Como último recurso, si no hay interfaces loopback ni IDs explícitos, el [[Router ID]] lo determinará la dirección [[IPv4]] activa más alta de sus interfaces físicas. |

![[Pasted image 20260309212326.png]]

## Configurar prioridad
Para modificar la jerarquía en la elección de los routers [[DR]] y [[BDR]], se puede configurar la prioridad de manera manual utilizando el comando `ip ospf priority` directamente en la interfaz.
![[Pasted image 20260309213048.png]]
Para reiniciar el proceso de [[OSPF]] y forzar una nueva elección aplicando los cambios de prioridad, se emplea el comando `clear ip ospf process` en el modo privilegiado (Clear del CLI).
![[Pasted image 20260309213148.png]]
![[Pasted image 20260309213220.png]]