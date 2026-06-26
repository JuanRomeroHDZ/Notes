1. Cuando una red OSPF está convergida y un router no ha detectado ningún cambio en la topología de la red, ¿cada cuánto se enviarán paquetes LSU a los routers vecinos?
Despues de que todos los LSRs han sido existosos, la adjacencia de los routers son considerados sincronizados y en el estado *Full State*. Las actualizaciones LSUs son enviados a los vecinos solamente bajo las siguientes condiciones: 
a) Cuando la topología cambia
b) Cada 30mnts (Cuando no cambia)
2. ¿Qué paso del proceso de enrutamiento de estado de enlace se describe cuando un router construye una base de datos de estado de enlace basada en LSAs recibidos?
En el proceso de enrutamiento de estado de enlace generico, el tercer paso is construir la base del enlace de estado. Despues las advertencias del estado de enlace son recibidas del vecino adjacente, OSPF permite a los routers utilizar esa información para construir la tabla de topología *Topology Table (LSDB)* el cual contiene información sobre todos los demás routers en el area de red y representa la topología de red. Una vez que la base de datos esta sincronizada, entonces el router puede ejecutar el algoritmo SPF para encontrar el mejor camino.
3. ¿Qué tipo de paquete OSPFv2 contiene una lista abreviada de la LSDB de un router emisor y es utilizado por los routers receptores para verificarla contra su LSDB local?
La descripción del paquete de la base de datos contiene una lista abreviada de la base de datos enviada por un router vecino para que el router receptor pueda verificar de nuevo la base de datos local
4. 

| #       | State         |
| ------- | ------------- |
| First   | Down          |
| Second  | Init          |
| Third   | Two way state |
| Fourth  | Exstart       |
| Fifth   | Exchange      |
| Sixth   | Loading       |
| Seventh | Full          |
Es más de logica de como inicia un proceso.
5. ![[Pasted image 20260625224822.png]]
Se supone que el orden por el que empieza es: 1. Prioridad, 2. ID, 3. IP, 4. Loopback IP
En esta ocasión tenemos:

| Name | Priority | ID      | IP               |
| ---- | -------- | ------- | ---------------- |
| R1   | 2        | 1.1.1.1 | 192.168.1.100/32 |
| R2   | 1        | 2.2.2.2 | 192.168.2.100/32 |
| R3   | 1        | 3.3.3.3 | 192.168.3.100/32 |
| R4   | 2        | 4.4.4.4 | 192.168.4.100/32 |
Como se puede observar, existen dos routers con la misma prioridad, en este caso se utilizará el ID para desempatar, por lo que tenemos que el router 4 para a DR y el router 1 pasa a ser el BDR
5. Cuales son los propositos principales del router ID en OSPF?
a) Identificar dentro del OSPF al router
b) Facilitar la participación en la elección del router designado
6.  Refer to the exhibit. What is the OSPF cost to reach the router A LAN 172.16.1.0/24 from B?
![[Pasted image 20260625230235.png]]

Para calcular el costo es necesario conocer una formula sencilla, el cual sería en esta ocasión: Reference bandwidth / interface bandwidth
La banda hancha de referencia es 10⁸ que esto es igual a 100,000,000, entonces sería: 100,000,000/1,544,000 dando el resultado de 64. Se puede sacar tambien: 1000 (GB) convirtiendolo a kbs = 1000 * 100, dando: 100,000 y luego entre 1544, dando un resultado de 64.7... En esta ocasión siempre se redondea para abajo, total: 64 y posteriormente se le suma 1 porque solo es 1 salto. Total: 65
5. Which command will a network engineer issue to verify the configured hello and dead timer intervals on a point-to-point WAN link between two routers that are running OSPFv2?
Considerando que el punto a punto se realiza en esta ocasión por serial, entonces sería show ip ospf interface serial 0/0/0
6. Refer to the exhibit. A network administrator has configured OSPFv2 on the two Cisco routers as shown. The routers are unable to form a neighbor adjacency. What should be done to fix the problem?
![[Pasted image 20260625231435.png]]
Como se puede observar, la red del serial 0/0 tiene 192.168.20.0/30, el router R2 cuenta con la ip 192.168.20.5, por eso es que no lo encuentra, el serial śolo permite un par para la conexión, en esta ocasión se debe cambiar 192.168.20.2 para el router R2
7. What is a feature of an IPS
Para que esta sea una respuesta sencilla, debemos comprender que es un IPS, en eta ocasión IPS significa *Intrusion Prevention System*  el cual ayuda a monitorear actividad maliciosa.
8. 