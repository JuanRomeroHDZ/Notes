NAT basicamente trabaja bajo traducciones en las que la red interna esta sujeta a traduccion. Las red externa se refiere a las otras redes.

NAT tiene cuatro tipos de direcciones IPv4:

- Direccion local interna
- Direccion Global Interna
- Direccion Local externa
- Direccion Global externa.

Al determinar qué tipo de dirección se utiliza, es importante recordar que la terminología de NAT siempre se aplica desde la perspectiva del dispositivo con la dirección traducida:

· Dirección interna: - la dirección del dispositivo que NAT está traduciendo.
. Dirección externa: - la dirección del dispositivo de destino.

NAT tambien usa los conceptos de local o global con relacion a las direcciones:

. Dirección local: -una dirección local es cualquier dirección que aparece en la parte interna de la red.
. Dirección global: - una dirección global es cualquier dirección que aparece en la parte externa de la red.

Los terminos "interna" y "externa" se combinan con los terminos "global" y "local" para hacer referencia a direcciones especificas. El enrutador NAT, R2 en la figura, es el punto de demarcación entre las redes internas y externas. R2 está configurado con un grupo de direcciones públicas
para asignar a los hosts internos. Consulte la tabla de red y NAT de la figura para obtener la siguiente explicacion de cada uno de los tipos dedirecciones NAT.

![[Pasted image 20260411224702.png]]