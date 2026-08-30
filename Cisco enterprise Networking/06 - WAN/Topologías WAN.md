---
tipo: [[WAN]]
tema: Topologías WAN
estado: Completado
region: [[Parietal]]
---
# [[WAN Topologies|Topologías WAN]]
En el mundo de las WAN existen varias topologías muy complejas de comprender, tomando en cuenta que la mayoría no las podemos ver. De tal manera, se toman en cuenta las topologías lógicas, lo que permite interpretar cómo funciona una red WAN. En el mundo real, las redes WAN funcionan con varias de las siguientes o una combinación entre ellas.

 
| Topología WAN | Características Principales | Ventajas / Desventajas |
| :--- | :--- | :--- |
| **[[Punto a Punto]]** | Conexiones dedicadas de línea arrendada. Servicio de transporte de Capa 2 transparente para la red del cliente. | Parece un vínculo físico directo entre extremos. / Puede resultar costoso si se requieren muchas conexiones. |
| **[[Hub and Spoke]] (Estrella)** | Una sola interfaz en el hub es compartida por todos los circuitos. Los spokes se interconectan a través del hub mediante circuitos virtuales. | Permite optimizar interfaces compartidas. / El hub representa un único punto de falla; si este falla, la comunicación cae. |
| **[[Dual-Homed\|Doble Conexión]]** | Dos routers hub conectados en redundancia a múltiples routers spoke a través de la nube WAN. | Ofrece redundancia de red, equilibrio de carga y enlaces de respaldo. / Es más cara por el hardware adicional y más difícil de implementar. |
| **[[Fully Meshed\|Completamente Mallada]]** | Utiliza varios circuitos virtuales para conectar absolutamente todos los sitios entre sí. | Es la topología más tolerante a fallos. Si un sitio pierde conectividad directa, puede desviar los datos a través de otros nodos. |
| **[[Partially Meshed\|Parcialmente Mallada]]** | Conecta muchos sitios de la red, pero no a todos de forma directa. | Permite un equilibrio de redundancia en nodos centrales sin el costo de una malla completa para los sitios secundarios. |
 

## Topología Punto a Punto
Los enlaces punto a punto a menudo implican conexiones dedicadas de línea arrendada desde el punto de borde corporativo hasta las redes de proveedores. Una conexión punto a punto implica un servicio de transporte de capa 2 a través de la red del proveedor de servicios. Los paquetes enviados desde un sitio se entregan a otro sitio y viceversa. Una conexión punto a punto es transparente para la red del cliente. Parece como si hubiera un vínculo físico directo entre dos puntos finales. Puede resultar costoso si se requieren many conexiones punto a punto.

![[Pasted image 20260429214759.png]]

## Topología de Estrella (Hub and Spoke)
Una topología de estrella (hub and spoke) permite que una sola interfaz al hub pueda ser compartida por todos los circuitos de radio. Los spoke routers se pueden interconectar a través del sitio de hub mediante circuitos virtuales y subinterfaces enrutadas del hub. La figura muestra una topología de estrella, que consta de tres spoke routers conectados a un hub router a través de una nube WAN.

Una topología de estrella (hub and spoke) también es un ejemplo de una topología de conexión única. Solo hay un hub router y toda la comunicación debe pasar por él. Por lo tanto, los routers radiales solo pueden comunicarse entre sí a través del hub router. En consecuencia, el hub router representa un único punto de falla. Si falla, la comunicación entre radios también falla.

![[Pasted image 20260429214912.png]]

## Topología de Doble Conexión
Una topología de doble conexión proporciona redundancia. Como se muestra en la figura, dos hub routers son de doble conexión, están conectados en redundancia a tres spoke routers a través de una nube WAN.

Sin embargo, la ventaja de las topologías de doble conexión es que ofrecen redundancia de red, equilibrio de carga, computación o proceso distribuido mejorados, y la capacidad de implementar las conexiones del proveedor de servicio de respaldo.

La desventaja es que son más caras de implementar que las topologías de conexión simple. Esto es porque requieren hardware de red, como routers y switches adicionales. Las topologías de doble conexión son más difíciles de implementar porque requieren configuraciones adicionales y complejas.

![[Pasted image 20260429215659.png]]

## Topología Fully Meshed (Completamente Mallada)
Una topología completamente mallada utiliza varios circuitos virtuales para conectar todos los sitios, como se muestra en la figura.

Esta es la topología más tolerante a fallos de las cinco mostradas. Por ejemplo, si el sitio B pierde conectividad con el sitio A, podría enviar los datos a través del sitio C o del sitio D.

![[Pasted image 20260429215755.png]]

## Topología Partially Meshed (Parcialmente Mallada)
Una topología parcialmente mallada conecta muchos sitios, pero no todos. Por ejemplo, en la figura, los sitios A, B y C todavía están completamente mallados. El sitio D debe conectarse al sitio A para llegar a los sitios B y C.

![[Pasted image 20260429215834.png]]