

Las ACL definen el conjunto de reglas que proporcionan un control mas optimo sobre los paquetes que ingresan o salenb por lsa interfaces que se retransmiten atravez del router.
para determinar que paquetes entran o salen se determina mediante la configuracion de las mismas.

![[Pasted image 20260406125046.png]]


Las ACL no actuan sobre los paquets que se generen o se originen en el mismo router.

Una ACL  de entrada correctemente configurada filtra los paquetes antes de que se enruten en la interfaz saliente. Las ACL de entrada son muy frecuentes , de tal manera qyue ahorra la sobrecarga de enrutar busquedas si el paquete se descarta. en caso de que las ACL permitan el paquete, el paquete se pasa al routing . como tal las ACL de entrada son indeales para lograr filtrar paquetes cuando la red conectada a una interfaz de entrada, en ese caso es el unico origen de los paquetes que se deben examinar.


Las ACL de salida  filtran los paquetes despues de que se enrutan , independientemente de la interfaz de entrafa. los paquetes que se enrutan a la interfaz saliente. luego se procesan a travez de la ACL saliente. las ACL de salida son las ideales cvuando se tiene que aplicar el mismo filtro a varias interfaces de entrada antes de salir por la misma interfaz de salida. asi en vez de configurar una por una solo configuras la de salida.

#### Procedimiento de una ACL

Cuando se aplica una ACL a una interfaz , esta siguen un procedimeinto operativo especifico . pro ejemplo se indican los pasos operativos que sigue el paquete .

1. El enrutador extrae la dirección IPv4 de origen del encabezado del paquete.
2. El enrutador comienza en la parte superior de la ACL y compara la dirección IPv4 de origen con cada ACE en un orden secuencial.
3. Cuando se hace una coincidencia, el enrutador lleva a cabo la instrucción, ya sea permitiendo o rechazando el paquete, y las ACE
restantes en la ACL, si las hay, no se analizan.
4. Si la direccion IPv4 de origen no coincide con ninguna ACE de la ACL, el paquete se descarta porque hay una ACE de denegación
implícita aplicada automáticamente a todas las ACL.

La última declaración ACE de una ACL es siempre una denegación implícita que bloquea todo el tráfico. De forma predeterminada, esta
instruccion se implica automaticamente al final de una ACL aunque esté oculta y no se muestre en la configuración.

Nota: Una ACL debe tener al menos una instruccion permit, de lo contrario, se denegara todo el trafico debido a la sentencia deny ACL implícita.