
Cuando se realiza la configuración de OSPF de área única, se deberán corroborar las configuraciones para saber si se hizo de la manera correcta. en esta nota se verán comandos para verificarla y ver su funcionamiento.



### Verificar Enrutamiento

- show ip interface brief
Este comando es para verificar las interfaces deseadas que esten acticas con el direccionamineto IP correcto.

![[Pasted image 20260318200129.png]]
- show ip route
Este comando es para poder verificar que la tabla de enrutaminento contiene todas las rutas esperadas.

![[Pasted image 20260318200536.png]]![[Pasted image 20260318200553.png]]




### Comandos Adicionales.

- **show ip ospf neighbor**
este comando muestra la lista de adyacencia que a creado con el ospf mostrando datos en concreto. en caso de que no muestra el router id o el estado en full significa que no creo un adyacencia OSPFv2
R1# **show ip ospf neighbor**

Neighbor ID     Pri   State           Dead Time   Address         Interface

3.3.3.3           0   FULL/  -        00:00:19    10.1.1.13       GigabitEthernet0/0/1

2.2.2.2           0   FULL/  -        00:00:18    10.1.1.6        GigabitEthernet0/0/0

R1#

- **show ip protocols**
Este comando muestra una version rapida de la informacio vital de la configuracion vital de OSPF, esta misma llega a inlcuir el ID de OSPFv2 , el router id , interfaces configradas para anunciar el router ospf, junto con lo vecinos ospf con el tiempo de actualizacion y la distancia administrativa.

R1# **show ip protocols**

*** IP Routing is NSF aware ***

(output omitted)

Routing Protocol is "ospf 10"

  Outgoing update filter list for all interfaces is not set

  Incoming update filter list for all interfaces is not set

  Router ID 1.1.1.1

  Number of areas in this router is 1. 1 normal 0 stub 0 nssa

  Maximum path: 4

  Routing for Networks:

  Routing on Interfaces Configured Explicitly (Area 0):

    Loopback0

    GigabitEthernet0/0/1

    GigabitEthernet0/0/0

  Routing Information Sources:

    Gateway         Distance      Last Update

    3.3.3.3              110      00:09:30

    2.2.2.2              110      00:09:58

  Distance: (default is 110)

R1#


- **show ip ospf**
El **show ip ospf** comando también se puede usar para examinar la ID del proceso OSPFv2 y el router ID, como se muestra en el siguiente resultado. Este comando muestra información de área OSPFv2 y la última vez que se ejecuto el algoritmo SPF.

R1# **show ip ospf**     

  Routing Process "ospf 10" with ID 1.1.1.1

  Start time: 00:01:47.390, Time elapsed: 00:12:32.320

  Supports only single TOS(TOS0) routes

  Supports opaque LSA

  Supports Link-local Signaling (LLS)

  Supports area transit capability

  Supports NSSA (compatible with RFC 3101)

  Supports Database Exchange Summary List Optimization (RFC 5243)

  Event-log enabled, Maximum number of events: 1000, Mode: cyclic

  Router is not originating router-LSAs with maximum metric

  Initial SPF schedule delay 5000 msecs

  Minimum hold time between two consecutive SPFs 10000 msecs

  Maximum wait time between two consecutive SPFs 10000 msecs

  Incremental-SPF disabled

  Minimum LSA interval 5 secs

  Minimum LSA arrival 1000 msecs

  LSA group pacing timer 240 secs

  Interface flood pacing timer 33 msecs

  Retransmission pacing timer 66 msecs

  EXCHANGE/LOADING adjacency limit: initial 300, process maximum 300

  Number of external LSA 1. Checksum Sum 0x00A1FF

  Number of opaque AS LSA 0. Checksum Sum 0x000000

  Number of DCbitless external and opaque AS LSA 0

  Number of DoNotAge external and opaque AS LSA 0

  Number of areas in this router is 1. 1 normal 0 stub 0 nssa

  Number of areas transit capable is 0

  External flood list length 0

  IETF NSF helper support enabled

  Cisco NSF helper support enabled

  Reference bandwidth unit is 10000 mbps

    Area BACKBONE(0)

        Number of interfaces in this area is 3

        Area has no authentication

        SPF algorithm last executed 00:11:31.231 ago

        SPF algorithm executed 4 times

        Area ranges are

        Number of LSA 3. Checksum Sum 0x00E77E

        Number of opaque link LSA 0. Checksum Sum 0x000000

        Number of DCbitless LSA 0

        Number of indication LSA 0

        Number of DoNotAge LSA 0

        Flood list length 0

R1#


- **show ip ospf interface**

este comando muestra una lista a detalle de las interfacez que tienen ospfv2 habilitada, o tambien especifica un intefaz para que te muestra la configuracion de esa itnerfaz, mostrando el router id local, tipo de red, costo , informacion de DR y BDR. etc.

R1# **show ip ospf interface GigabitEthernet 0/0/0**

GigabitEthernet0/0/0 is up, line protocol is up

  Internet Address 10.1.1.5/30, Area 0, Attached via Interface Enable

  Process ID 10, Router ID 1.1.1.1, Network Type POINT_TO_POINT, Cost: 10

  Topology-MTID    Cost    Disabled    Shutdown      Topology Name

        0           10        no          no            Base

  Enabled by interface config, including secondary ip addresses

  Transmit Delay is 1 sec, State POINT_TO_POINT

  Timer intervals configured, Hello 5, Dead 20, Wait 20, Retransmit 5

    oob-resync timeout 40

    Hello due in 00:00:01

  Supports Link-local Signaling (LLS)

  Cisco NSF helper support enabled

  IETF NSF helper support enabled

  Index 1/2/2, flood queue length 0

  Next 0x0(0)/0x0(0)/0x0(0)

  Last flood scan length is 1, maximum is 1

  Last flood scan time is 0 msec, maximum is 0 msec

  Neighbor Count is 1, Adjacent neighbor count is 1

    Adjacent with neighbor 2.2.2.2

  Suppress hello for 0 neighbor(s)

R1#



Para obtener un resumen rápido de las interfaces habilitadas para OSPFv2, utilice el **show ip ospf interface brief** comando, como se muestra en el siguiente resultado del comando. Este comando es útil para ver información importante, incluida la siguiente:

- Las interfaces están participando en OSPF
- Redes que se anuncian (Dirección IP/Máscara)
- Coste de cada enlace
- Estado de la red
- Número de vecinos en cada enlace
- 
R1# **show ip ospf interface brief**

Interface    PID   Area            IP Address/Mask    Cost  State Nbrs F/C

Lo0          10    0               10.10.1.1/24       10    P2P   0/0

Gi0/0/1      10    0               10.1.1.14/30       30    P2P   1/1

Gi0/0/0      10    0               10.1.1.5/30        10    P2P   1/1

R1#