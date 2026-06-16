
La tabla LSDB (_Link-State Database)_ o Base de Datos de Estado de Enlace) es una base de datos topológica utilizada por protocolos de estado de enlace como OSPF e IS-IS, que almacena todos los Anuncios de Estado de Enlace (LSA) recibidos. Todos los routers en un área OSPF sincronizan su LSDB para tener una vista idéntica y completa de la topología de la red. 

**Características clave de la LSDB:**

- **Mapa de la Red:** La LSDB representa la estructura completa de la red, permitiendo a los enrutadores conocer todos los demás nodos.
- **Sincronización:** Los routers inundan LSA para asegurar que todos los dispositivos dentro de un área mantengan una LSDB idéntica.
- **Base para SPF:** Los enrutadores utilizan la información de la LSDB para ejecutar el algoritmo SPF (Shortest Path First) de Dijkstra y calcular las mejores rutas.
- **Comando de visualización:** Se puede verificar su contenido con el comando `show ip ospf database`.
- **Composición:** Contiene varios tipos de LSA (1 a 5) que describen routers, redes y prefijos externos. 

La LSDB es crucial porque permite que cada router tenga un conocimiento detallado del entorno, permitiendo una convergencia rápida y la selección independiente de las rutas más cortas.