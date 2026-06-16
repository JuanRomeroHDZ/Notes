


**Router ID OSPF**

El OSPFv2 se habilita usando el comando **router ospf** _process-id_ del modo de configuración global. El valor _process-id_ representa un número entre 1 y 65.535 y lo selecciona el administrador de la red. El identificador de OSPF router ID es un valor de 32 bits, representado como una dirección IPv4. Un router habilitado para OSPF utiliza el ID del router para sincronizar las bases de datos OSPF y participar en la elección de DR y BDR. Los routers Cisco derivan el router ID según uno de los tres criterios, en el siguiente orden preferencial:

1. El router ID se configura explícitamente utilizando el comando de configuración OSPF **router-id** _rid_ router El valor _rid_ es cualquier valor de 32 bits expresado como una dirección IPv4.
    
2. Si el router ID no se configura explícitamente, el router elige la dirección IPv4 más alta de cualquiera de las interfaces loopback configuradas.
    
3. Si no se configuró ninguna interfaz loopback, el router elige la dirección IPv4 activa más alta de cualquiera de sus interfaces físicas.
    

El router ID se puede asignar a una interfaz de loopback. La dirección IPv4 para este tipo de interfaz loopback debe configurarse utilizando una máscara de subred de 32 bits (255.255.255.255), creando una ruta de host. Una ruta de host de 32 bits no se anunciaría como una ruta a otros routers OSPF. Después de que un router selecciona el router ID, un router OSPF activo no permitirá que el router ID cambie, hasta que el router se reinicie o el proceso de OSPF sea restablecido. Utilice el **clear ip ospf process** comando para restablecer las adyacencias. A continuación, puede verificar que R1 esté utilizando el nuevo router ID con el **show ip protocols** comando filtrado ara mostrar sólo la sección router ID.

**Redes OSPF punto a punto**

El comando de red se usa para determinar qué interfaces participan en el proceso de enrutamiento para un área OSPFv2. La sintaxis básica del **network** comando es **network** _network-address wildcard-mask_ **area** _area-id_. Cualquier interfaz de un router que coincida con la dirección de red del **network** comando puede enviar y recibir paquetes OSPF. Al configurar OSPFv2 de área única, el **network** comandodebe configurarse con el mismo valor _area-id_ en todos los routers. El wildcard mask suele ser la inversa de la máscara de subred configurada en esa interfaz. En el wildcard mask:

- **Wildcard mask bit 0** - coincide con el valor de bit correspondiente en la dirección.
    
- **Wildcard mask bit 1** - omite el valor del bit correspondiente en la dirección.
    

Dentro del modo de configuración de enrutamiento, hay dos formas de identificar las interfaces que participarán en el proceso de enrutamiento OSPFv2. Una forma es cuando el wildcard mask identifica la interfaz en función de las direcciones de red. Cualquier interfaz activa configurada con una dirección IPv4 perteneciente a esa red, participará en el proceso de enrutamiento OSPFv2. La otra forma es, que OSPFv2 se puede habilitar especificando la dirección IPv4 exacta de la interfaz, usando el wildcard mask cuádruple cero. Para configurar OSPF directamente en la interfaz, utilice el comando **ip ospf** interface configuration La sintaxis es **ip ospf** _process-id_ **area** _area-id_. El envío de mensajes innecesarios en una LAN afecta a la red mediante el uso ineficiente del ancho de banda y los recursos, y crea un mayor riesgo de seguridad. Use el **passive-interface** comando del modo de configuración del router para detener la transmisión de mensajes de enrutamiento a través de una interfaz de router, pero aún así permitir que esa red se anuncie a otros routers A continuación, el **show ip protocols** comando se utiliza para comprobar que la interfaz Loopback 0 aparece como pasiva. El proceso de elección de DR/ BDR es innecesario ya que solo puede haber dos routers en la red punto a punto entre R1 y R2. Utilice el comando interface configuration **ip ospf network point-to-point** en todas las interfaces en las que desee deshabilitar el proceso de elección DR/BDR. Utilice loopbacks para simular más redes de las que puede soportar el equipo. De forma predeterminada, las interfaces loopback se anuncian como rutas de host/32. Para simular una LAN real, la interfaz Loopback 0 se configura como una red punto a punto.


**Tipos de redes OSPF**

Los routers se pueden conectar al mismo switch para formar una red multiacceso. Las LAN Ethernet son el ejemplo más común de redes broadcast con multiacceso. En las redes braodcast, todos los dispositivos en la red pueden ver todas las tramas broadcast y multicast. El DR es responsable de recolectar y distribuir las LSA. El DR usa la dirección IPv4 multicast 224.0.0.5 que está destinada a todos los routers OSPF. Si el DR deja de producir paquetes Hello, el BDR se asciende a sí mismo y asume la función de DR. Todos los otros routers se convierten en DROTHER. Los DROTHER utilizan la dirección de acceso múltiple 224.0.0.6 (todos los routers designados) para enviar paquetes OSPF al DR y al BDR. Sólo DR y BDR escuchan 224.0.0.6. Para verificar los roles del router OSPFv2, use el **show ip ospf interface** comando. Para comprobar las adyacencias OSPFv2, use el **show ip ospf neighbor** comando. El estado de los vecinos en las redes de acceso múltiple puede ser:

- **FULL/DROTHER** - Este es un router DR o BDR que está completamente adyacente con un router que no sea DR o BDR.
    
- **FULL/DR** - El router está completamente adyacente con el vecino DR indicado.
    
- **FULL/BDR** - El router está completamente adyacente con el vecino BDR indicado.
    
- **2-WAY/DROTHER** - El router que no es DR o BDR tiene una relación vecina con otro router no DR o BDR.
    

La decisión de elección del DR y el BDR OSPF se hace según los siguientes criterios, en orden secuencial:

1. Los routers en la red seleccionan como DR al router con la prioridad de interfaz más alta. El router con la segunda prioridad de interfaz más alta se elige como BDR. La prioridad puede configurarse para que sea cualquier número entre 0 y 255. Si el valor de prioridad de la interfaz se establece en 0, esa interfaz no se puede elegir como DR ni BDR. La prioridad predeterminada de las interfaces broadcast de acceso múltiple es 1. Por lo tanto, a menos que se configuren de otra manera, todos los routers tienen un mismo valor de prioridad y deben depender de otro método de diferenciación durante la elección del DR/BDR.
    
2. Si las prioridades de interfaz son iguales, se elige al router con la ID más alta como DR. El router con la segunda ID más alta es el BDR.
    

La elección del DR y del BDR para OSPF no se basa en derecho preferente. Si el DR falla, el BDR se asciende automáticamente a DR. Esto ocurre así, incluso si se agrega otro DROTHER con una prioridad o router ID más alta a la red después de la elección inicial de DR/BDR. Sin embargo, después de que un BDR es promovido a DR, se produce una nueva elección de BDR, y el DROTHER con la mayor prioridad o router ID se elige como el nuevo BDR. Para establecer la prioridad de una interfaz, utilice el comando **ip ospf priority** _value_, donde value es 0 a 255. Si el valor es 0, el router no se convertirá en DR o BDR. Si el valor es de 1 a 255, entonces el router con el valor de mayor prioridad probablemente se convertirá en DR o BDR en la interfaz.

**Modificar OSPFv2 de área única**

OSPF utiliza el costo como métrica. Cuando el costo es menor, la ruta es mejor que una con un costo mayor. El costo de Cisco de una interfaz es inversamente proporcional al ancho de banda de la interfaz. Por lo tanto, cuanto mayor es el ancho de banda, menor es el costo. La fórmula que utiliza para calcular el costo de OSPF es: Cost = reference bandwidth / interface bandwidth. Debido a que el valor del costo OSPF debe ser un número entero, las interfaces FastEthernet, Gigabit Ethernet y 10 GigE comparten el mismo costo. Para corregir esta situación, puede ajustar el ancho de banda de referencia con el **auto-cost reference-bandwidth** comando en cada router OSPF o establecer manualmente el valor de costo OSPF con el **ip ospf cost** comando. Para ajustar el ancho de banda de referencia, use el comando de configuración del router **auto-cost reference-bandwidthauto-cost reference-bandwidth Mb/s**. El costo de una ruta de OSPF es el valor acumulado desde un router hasta la red de destino. Los valores de costo OSPF se pueden manipular para influir en la ruta elegida por OSPF. Para cambiar el informe de valor de costo del router OSPF local a otros routers OSPF, utilice el comando de configuración de interfaz **ip ospf cost** _value_. Si el intervalo Dead caduca antes de que los routers reciban un paquete Hello, OSPF elimina ese vecino de su base de datos (LSDB). El router satura la LSDB con información acerca del vecino inactivo por todas las interfaces con OSPF habilitado. Cisco utiliza un valor predeterminado de 4 veces el intervalo Hello o 40 segundos en redes multiacceso y punto a punto. Para verificar el estado de la interfaz, utilice el comando **show ip ospf interface**. Los intervalos de Hello y Dead de OSPFv2 pueden modificarse manualmente mediante los siguientes comandos del modo de configuración de interfaces: **ip ospf hello-interval** _seconds_ and **ip ospf dead-interval** _seconds_.

**Propagación de ruta predeterminada**

En la terminología OSPF, el router ubicado entre un dominio de enrutamiento OSPF y una red que no es OSPF se llama ASBR. Para propagar una ruta predeterminada, el ASBR debe configurarse con una ruta estática predeterminada mediante el comando **ip route 0.0.0.0 0.0.0.0** [_next-hop-address_ | _exit-intf_] y el comando de configuración del **default-information originate** router. Esto indica al ASBR que sea la fuente de la información de ruta predeterminada y propague la ruta estática predeterminada en las actualizaciones de OSPF. Verifique la configuración de ruta predeterminada en el ASBR usando el **show ip route** comando.

---


**Verificar OSPFv2 de área única**

Los dos comandos siguientes se utilizan para verificar el enrutamiento:

- **show ip interface brief** : se utiliza para verificar que las interfaces deseadas estén activas con el direccionamiento IP correcto.
    
- **show ip route** - Se utiliza para comprobar que la tabla de enrutamiento contiene todas las rutas esperadas.
    

Entre los comandos adicionales para determinar que OSPF funciona como se esperaba se incluyen: **show ip ospf neighbor**, **show ip protocols**, **show ip ospf**, y **show ip ospf interface**.

Use el comando **show ip ospf neighbor** para verificar que el router ha formado una adyacencia con sus routers vecinos. Para cada vecino, este comando muestra lo siguiente:

- **Neighbor ID** - el rouuter ID del router vecino.
    
- **Pri** - la prioridad OSPFv2 de la interfaz. Este valor se utiliza en la elección del DR y del BDR.
    
- **State** - el estado de OSPFv2 de la interfaz. El estado FULL significa que el router y su vecino poseen LSDB de OSPFv2 idénticas. En las redes multiacceso, como Ethernet, dos routers adyacentes pueden mostrar sus estados como 2WAY. El guion indica que no se requiere ningún DR o BDR debido al tipo de red.
    
- **Dead Time** - el tiempo restante que el router espera para recibir un paquete Hello OSPFv2 del vecino antes de declararlo inactivo. Este valor se restablece cuando la interfaz recibe un paquete Hello.
    
- **Address** - la dirección IPv4 de la interfaz del vecino a la que el router está conectado directamente.
    
- **Interface** - la interfaz en la que este router formó adyacencia con el vecino.
    

El **show ip protocols** comando es una forma rápida de verificar la información vital de configuración de OSPF, como la ID del proceso OSPFv2, el router ID, las interfaces configuradas explícitamente para anunciar las rutas de OSPF, los vecinos desde los que el router recibe actualizaciones y la distancia administrativa predeterminada, que es 110 para OSPF. Use el **show ip ospf** comando para examinar la ID del proceso del protocolo OSPFv2 y el router ID. Este comando muestra información de área OSPFv2 y la última vez que se ejecuto el algoritmo SPF. El **show ip ospf interface** comando proporciona una lista detallada para cada interfaz habilitada para OSPFv2. Especifica una interfaz para una sola interfaz para mostrar el ID de proceso, el router ID local, el tipo de red, el costo OSPF, la información de DR y BDR en vínculos de acceso múltiple y vecinos adyacentes.
