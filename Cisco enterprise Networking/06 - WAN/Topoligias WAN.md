

En el mundo de las WAN existen varias topologías muy complejas de comprender, tomando en cuenta que la mayoria no las podemos ver, de tal manera se toman en cuenta las topologias logicas lo que permite interpretar como funciona una red WAN. en el mundo real las redes WAN funcionan con varias de las siguientes o combinacion entre ellas.


-  Topología punto a punto

Los enlaces punto a punto a menudo implican conexiones dedicadas de línea arrendada desde el punto de borde corporativo hasta las redes de proveedores. Una conexión punto a punto implica un servicio de transporte de capa 2 a través de la red del proveedor de servicios. Los paquetes enviados desde un sitio se entregan a otro sitio y viceversa. Una conexión punto a punto es transparente para la red del cliente. Parece como si hubiera un vínculo físico directo entre dos puntos finales.

Puede resultar costoso si se requieren muchas conexiones punto a punto.

![[Pasted image 20260429214759.png]]



- Topología de estrella (hub and spoke)

Una topología de estrella (hub and spoke) permite que una sola interfaz al hub puede ser compartida por todos los circuitos de radio. Spoke routers se pueden interconectar a traves del sitio de hub mediante circuitos virtuales y subinterfaces enrutadas del hub. La figura muestra una topología de estrella, que consta de tres spoke routers conectados un hub router a través de una nube WAN.

Una topología de estrella (hub and spoke) también es un ejemplo de una topología de conexión única. Solo hay un hub router y toda la comunicación debe pasar por él. Por lo tanto, los routers radiales solo pueden comunicarse entre sí a través del hub router. En consecuencia, el hub router representa un único punto de falla. Si falla, la comunicación entre radios también falla.

![[Pasted image 20260429214912.png]]



- Topología de doble conexión

Una topología de doble conexión proporciona redundancia. Como se muestra en la figura, dos hub routers son de doble conexión, están conectados en redundancia a tres spoke routers a través de una nube WAN.

Sin embargo, la ventaja de las topologías de doble conexión es que ofrecen redundancia de red, equilibrio de carga, computación o proceso distribuido mejorados, y la capacidad de implementar las conexiones del proveedor de servicio de respaldo.

La desventaja es que son más caros de implementar que las topologías de conexión simple Esto es porque requieren hardware de red, como routers y switches adicionales. Las topologías de doble conexión son más difíciles de implementar porque requieren configuraciones adicionales y complejas.

![[Pasted image 20260429215659.png]]



- Topología Fully Meshed

Una topología completamente mallada utiliza varios circuitos virtuales para conectar todos los sitios, como se muestra en la figura.

Esta es la topología más tolerante a fallos de las cinco mostradas. Por ejemplo, si el sitio B pierde conectividad con el sitio A, podría enviar los datos a traves del sitio C o del sitio D.

![[Pasted image 20260429215755.png]]




- Topología Partially Meshed

Una topología parcialmente mallada conecta muchos sitios, pero no todos. Por ejemplo, en la figura, los sitios A, B, C todavía están completamente mallados. El sitio D debe conectarse al sitio A para llegar a los sitios B y C.

![[Pasted image 20260429215834.png]]