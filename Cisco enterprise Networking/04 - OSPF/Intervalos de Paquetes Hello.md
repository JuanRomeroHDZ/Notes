---
tipo: [[OSPF]]
tema: Intervalos de los Paquetes de Hello
estado: Completado
region: [[Parietal]]
---
# [[OSPF Hello Intervals]]
El [[OSPF Hello Packet|paquete Hello]] es el encargado de verificar la actividad de los vecinos. Si un router deja de recibir estos paquetes, el [[DR]] eliminará al router inactivo de su [[Link State Database|LSDB]].

## Temporizadores por defecto
Por defecto, el temporizador de [[Hello Packet|Hello]] es de 10 segundos. El temporizador de [[Dead Interval|muerte]] (Dead) se calcula como cuatro veces el valor del Hello (40 segundos). 

Es posible modificar estos tiempos para ajustar la convergencia de la red, por ejemplo, a un estándar de 30 segundos de Hello y 120 segundos de Dead.

| Temporizador | Comando |
| :--- | :--- |
| Hello Interval | `Router(config-if)# ip ospf hello-interval [seconds]` |
| Dead Interval | `Router(config-if)# ip ospf dead-interval [seconds]` |

> Nota: Al modificar estos valores manualmente, todos los routers en el segmento de red deben tener configurados los mismos intervalos, de lo contrario, la adyacencia [[OSPF]] no se formará.

![[Pasted image 20260317195417.png]]