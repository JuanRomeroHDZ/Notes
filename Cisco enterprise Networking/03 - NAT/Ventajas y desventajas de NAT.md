
Ventajas de NAT

NAT resuelve nuestro problema de no tener suficientes direcciones IPv4, pero también puede crear otros problemas. Este tema aborda las
ventajas y desventajas de NAT.

NAT proporciona muchos beneficios, incluidos los siguientes:

- NAT conserva el esquema de direccionamiento legalmente registrado al permitir la privatización de las intranets. NAT conserva las direcciones mediante la multiplexación de aplicaciones en el nivel de puerto. Con la sobrecarga NAT (PAT), los hosts internos pueden compartir una única dirección IPv4 publica para todas las comunicaciones externas. En este tipo de configuración, se requieren muy pocas direcciones externas para admitir varios hosts internos.
- NAT aumenta la flexibilidad de las conexiones a la red publica. Se pueden implementar varios conjuntos y conjuntos de respaldo y de equilibrio de carga para asegurar conexiones de red pública confiables.
- NAT proporciona coherencia a los esquemas de direccionamiento de red interna. Para cambiar el esquema de direcciones IPv4 publicas en una red que no utiliza direcciones IPv4 privadas ni NAT, se requiere redireccionar todos los hosts en la red existente. Los costos de redireccionamiento de hosts pueden ser considerables. NAT permite mantener el esquema de direcciones IPv4 privadas existente a la vez que facilita el cambio a un nuevo esquema de direccionamiento publico. Esto significa que una organización podría cambiar los ISP sin necesidad de modificar ninguno de sus clientes internos.
- Usando direcciones IPv4 RFC 1918, NAT oculta las direcciones IPv4 de los usuarios y otros dispositivos. Algunas personas consideran esto una característica de seguridad; sin embargo, la mayoría de los expertos están de acuerdo en que NAT no proporciona seguridad. Un firewall con detección de estado es lo que brinda seguridad al perímetro de la red.


Desventajas de la NAT

NAT tiene inconvenientes. El hecho de que los hosts en Internet parezcan comunicarse directamente con el dispositivo habilitado para NAT, en
lugar de con el host real dentro de la red privada, crea una serie de problemas.

Una desventaja del uso de NAT se relaciona con el rendimiento de la red, en especial, en el caso de los protocolos en tiempo real como VolP.NAT aumenta los retrasos de reenvió porque la traducción de cada direccion IPv4 dentro de los encabezados de los paquetes lleva tiempo. Al
primer paquete siempre se aplica el switching de procesos por la ruta mas lenta. El router debe revisar todos los paquetes para decidir si necesitan traducción. El router debe modificar el encabezado de IPv4 y, posiblemente, el encabezado TCP o UDP. El checksum del encabezado
de IPv4, junto con el checksum de TCP o UDP, se debe volver a calcular cada vez que se realiza una traducción. Si existe una entrada de caché, el resto de los paquetes atraviesan la ruta de switching rápido; de lo contrario, también se retrasan.

Esto se vuelve mas un problema a medida que los grupos de direcciones IPv4 publicas para ISP se agotan. Muchos ISP tienen que asignar a los clientes una dirección IPv4 privada en lugar de una dirección IPv4 publica. Esto significa que el router del cliente traduce el paquete de su
dirección IPv4 privada a la dirección IPv4 privada del ISP. Antes de reenviar el paquete a otro proveedor, el ISP realizará NAT de nuevo, traduciendo sus direcciones IPv4 privadas a una de sus pocas direcciones IPv4 publicas. Este proceso de dos capas de traducción NAT se
conoce como Carrier Grade NAT (CGN).

Otra desventaja del uso de NAT es que se pierde el direccionamiento de extremo a extremo. Esto se conoce como el principio de extremo a extremo. Muchos protocolos y aplicaciones de Intemet dependen del direccionamiento de extremo a extremo desde el origen hasta el destino.
Algunas aplicaciones no funcionan con NAT. Por ejemplo, algunas aplicaciones de seguridad, como las firmas digitales, fallan porque la dirección IPv4 de origen cambia antes de llegar a destino. Las aplicaciones que utilizan direcciones físicas, en lugar de un nombre de dominio
calificado, no llegan a los destinos que se traducen a través del Router NAT. En ocasiones, este problema se puede evitar al implementar las asignaciones de NAT estática.

También se reduce el seguimiento IPv4 de extremo a extremo. El seguimiento de los paquetes que pasan por varios cambios de dirección a través de varios saltos de NAT se torna mucho mas difícil y, en consecuencia, dificulta la resolución de problemas.

El uso de NAT también genera complicaciones en la utilización de protocolos de tunneling, como IPsec, porque NAT modifica valores en los encabezados, lo que hace fallar las comprobaciones de integridad

Los servicios que requieren que se inicie una conexión TCP desde la red externa, o "protocolos sin estado", como los servicios que utilizan UDP, pueden interrumpirse. A menos que el Router NAT este configurado para admitir dichos protocolos, los paquetes entrantes no pueden llegar a su destino. Algunos protocolos pueden acomodar una instancia de NAT entre los hosts participantes (FTP en modo pasivo, por ejemplo), pero fallan cuando NAT separa ambos sistemas de Internet.
