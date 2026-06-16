tipos de paquetes:

- Hello 
Descubre Vecinos y construye las adyasencias entre ellos.

- Databa Description (DBD)

Controla la sincronizan de las bases de datos entre los routers

- Link-State Request (LSR)
Solicita los resgistro especificos de estado de enlace de router a router.

- Link-State Update (LSU)
Envía los registros de estado de enlace específicamente solicitados, es una respuesta del paquete "LSR"

- Link_State Acknowledgment (LSAck)

Reconoce los demas tipos de los paquetes. cuando se recibe una LSU, el router envía un LSAck para confirmar la recepción de la LSU. El campo de datos del LSAck está vacío.


Los paquetes de estado de vinculo son la herramientas principalmente utilizada por OSPF para ayudar a determinar la ruta mas rapida disponible para un paquete. OSPF utiliza los paquetes de estado de enlace (LSP) para establecer y mantener las adyacencias de los vecinos , así como para lograr intercambiar las actualizaciones del enrutamiento. por eso cada paquete cumple una función especifica en el proceso de enrutamiento de OSPF.

![[Pasted image 20260208165017.png]]


##### Actualizaciones de estado de enlace.

**Estado de enlace** es un algoritmo de enrutamiento utilizado en redes informáticas para determinar el mejor camino para que los paquetes de datos viajen desde una fuente hasta un destino.  A diferencia de otros métodos, como el vector distancia, el estado de enlace permite a cada router construir un **mapa detallado de la topología completa de la red**, lo que facilita cálculos más precisos y eficientes del camino más corto.


Los routers principalmente intercambian paquetes DBD del tipo 2, que es una lista breviada de la LSBD del router emisor. Usualmente se emplean al recibir routers para verificar con el LSDB local.

Los routers que juegan el papel de receptores usan los paquetes LSR de tipo 3 para solicitar mas información acerca de una entrada de la DBD.
El paquete LSU de tipo 4 se Usa mas que nada para responder el paquete LSU de tipo 4 , dándole la información requerida.

Los paquetes LSU tambien se pueden usar para reenviar actualización de la red de routing OSPF , como los cambios de estado de enlace. específicamente , un paquete LSU puede contener 11 tipos diferentes de LSA OSPFv2. Con algunos de los paquetes mas comunes son lo siguiente. En OSPFv3 cambio el nombre de varias de estas LSA y también contiene dos LSA adicionales.

Algo importante para evitar confucion entre LSU y LSA, mas que nada es que una LSU contiene Uno o mas LSA.![[Pasted image 20260208170845.png]]



##### Paquete HELLO

El paquete de OSPF tipo 1 es el paquete HELLO . El paquete Hello se usa para hacer lo siguiente.


