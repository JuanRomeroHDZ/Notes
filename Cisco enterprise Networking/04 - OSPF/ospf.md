


El [OSPF] (Open Shortest Path First) es un protocolo de enrutamiento dinámico de estado de enlace diseñado para las redes IP. el cual opera en sistema autónomo, utiliza el algoritmo de Dijkstra para determinar la ruta mas rápida y eficiente, ofreciendo una convergencia rápida y escalabilidad en redes grandes, el OSPF emplea un algoritmo para mandar paquetes haciendo los mensos saltos posibles no tomando una mejor siendo larga.

El OSPF v2 se emplea para redes ipv4. OSPF V3 se emplea en la redes IPv6.
el protocolo OSPF es un protocolo de enrutamiento de [[Estado de enlace]] que se desarrollo como una alternativa a el protocolo de información de enrutamiento de Distancia (RIP). RIP fue un protocolo de enrutamiento aceptable en los primeros días de las redes e internet, lo cual sin embargo el hecho de que RIP dependiera del conteo de saltos como única métrica para determinar la mejor ruta disponible , así rápidamente se volvió problemático. En el conteo de los saltos debido a que no escalaba bien en redes mas grandes con varias rutas de distintas velocidades. El OSPF tiene ventajas significativas sorbe el RIP  en el sentido que ofrece una mejor [[Convergencia]] mas rápida. y el cual se escala a implementaciones de redes mucho mas grandes.

![[Pasted image 20260207212431.png]]

Los mensajes que OSPF utiliza para crear y mantener tres bases de datos OSPF , como se muestra:

- Base de datos de adyacencia - crea la tabla de vecinos.
- Base de datos de estado de enlace (LSDB) - crea la tabla de topología.
- Base de datos de reenvío - crea la tabla de enrutamiento.

Estas tablas en particular muestran un lista de los Routers vecinos para intercambiar información de enrutamiento. Estas tablas se almacenan y se mantienen en la RAM.

![[Pasted image 20260207212417.png]]


Para que OSPF sea mas eficaz y escalable , este protocolo admite enrutamiento jerárquico mediante las áreas. Un área en OSPF es un grupo de routers que comparten la misma información de estado de enlace en sus [[LSDB]] , el OSPF se pude implementar de una de estas dos maneras:

- OSPF de área única = rodos lo enrutadores que se encuentran en la área . Una buena practica es usar el área 0.
![[Pasted image 20260207214236.png]]
- OSPF Multitarea = OSPF se implementa mediante varias áreas, de manera jerárquica. todas las áreas deben conectarse al área troncal (área 0). los routers que se han interconectado en las áreas se denominan  "Routers Fronterizos de Área" (ABR)

![[Pasted image 20260207214248.png]]