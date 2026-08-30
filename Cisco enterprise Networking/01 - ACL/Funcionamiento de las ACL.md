---
tipo: [[Access Control List]]
tema: Funcionamiento de las ACLs
estado: Completado
region: [[Parietal]]
---
# [[Funcionamiento de las ACLs]]
Las [[Access Control List|ACL]] definen el conjunto de reglas que proporcionan un control más óptimo sobre los paquetes que ingresan o salen por las interfaces que se retransmiten a través del router. Para determinar qué paquetes entran o salen, se determina mediante la configuración de las mismas.
![[Pasted image 20260406125046.png]]

Las [[Access Control List|ACL]] no actúan sobre los paquetes que se generen o se originen en el mismo router.

## [[Input ACL]]
Una [[Input ACL|ACL de entrada]] correctamente configurada filtra los paquetes antes de que se enruten en la interfaz saliente. Las [[Input ACL|ACL de entrada]] son muy frecuentes, de tal manera que ahorra la sobrecarga de enrutar búsquedas si el paquete se descarta. En caso de que las [[Access Control List|ACL]] permitan el paquete, el paquete se pasa al [[Routing]]. Como tal, las [[Input ACL|ACL de entrada]] son ideales para lograr filtrar paquetes cuando la red conectada a una interfaz de entrada, en ese caso, es el único origen de los paquetes que se deben examinar.

## [[Output ACL]]
Las [[Output ACL|ACL de salida]] filtran los paquetes después de que se enrutan, independientemente de la interfaz de entrada. Los paquetes que se enrutan a la interfaz saliente luego se procesan a través de la [[Output ACL|ACL saliente]]. Las [[Output ACL|ACL de salida]] son las ideales cuando se tiene que aplicar el mismo filtro a varias interfaces de entrada antes de salir por la misma interfaz de salida. Así, en vez de configurar una por una, solo configuras la de salida.

## [[Procedimiento de una ACL]]
Cuando se aplica una [[Access Control List|ACL]] a una interfaz, esta sigue un procedimiento operativo específico. Por ejemplo, se indican los pasos operativos que sigue el paquete:

1. El enrutador extrae la dirección [[IPv4]] de origen del encabezado del paquete.
2. El enrutador comienza en la parte superior de la [[Access Control List|ACL]] y compara la dirección [[IPv4]] de origen con cada [[ACE]] en un orden secuencial.
3. Cuando se hace una coincidencia, el enrutador lleva a cabo la instrucción, ya sea permitiendo o rechazando el paquete, y las [[ACE]] restantes en la [[Access Control List|ACL]], si las hay, no se analizan.
4. Si la dirección [[IPv4]] de origen no coincide con ninguna [[ACE]] de la [[Access Control List|ACL]], el paquete se descarta porque hay una [[Implicit Deny|ACE de denegación implícita]] aplicada automáticamente a todas las [[Access Control List|ACL]].

### [[Implicit Deny]]
La última declaración [[ACE]] de una [[Access Control List|ACL]] es siempre una [[Implicit Deny|denegación implícita]] que bloquea todo el tráfico. De forma predeterminada, esta instrucción se implica automáticamente al final de una [[Access Control List|ACL]] aunque esté oculta y no se muestre en la configuración.

> Nota: Una [[Access Control List|ACL]] debe tener al menos una instrucción permit, de lo contrario, se denegará todo el tráfico debido a la sentencia [[Implicit Deny|deny ACL implícita]].