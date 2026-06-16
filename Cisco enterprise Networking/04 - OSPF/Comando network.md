
Un tipo de red que emplea OSPF es la red punto a punto, este comando puede especificar las interfaces que pertenecen a una red punto a punto configurando correctamente el comando network. también se puede configurar OSPF directamente en la interfaz con el **ip ospf**.
 Sintaxis comando network: 


Router(config-router)# network network-address wildcard-mask area area-id

esta sintaxis de network-addres wildcard mask es para poder habilitar el ospf en la interfaces , todas la interfaces que contengan el ospf podran enviar y recibir paquetes ospf.

el valor de area-id se refiere al area de ospf lo cual es el identificador, del area, todos lo routers que esten en la red de ospf se tiene que asignar el mismo valor de ospf en todos los routers.
se recomienda como buena pratica el area con valor 0 con ospfv2. esto facilita que la red se modifique en el futuro al habilitar ospf multiarea.