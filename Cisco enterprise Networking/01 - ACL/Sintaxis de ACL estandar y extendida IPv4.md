

### Sintaxis ACL estándar (numerada , nombrada.)


#### ACL estándar numerada
En general para crear un ACL estándar numera se emplea el siguiente comando.


Router(config)# access-list access-list-number {deny | permit | remark text} source [ source-wildcard] [log]

![[Pasted image 20260406203755.png]]

![[Pasted image 20260406203819.png]]


#### ACL estándar nombrada

En cuanto a la funcion solo mejora del lado la verstibilidad ya qeu es mas facil identificarla de eta manera.

![[Pasted image 20260406204321.png]]

![[Pasted image 20260406204521.png]]



#### Aplicación de ACL estándar IPv4

Una vez se tenga la ACL configurada correctamente. se emplearía el siguiente comando dentro de la configuración de una interfaz previamente seleccionada.


![[Pasted image 20260406204813.png]]

Para eliminar una ACL de una interfaz, primero introduzca el comando de configuración de no ip access-group interface. Sin embargo, la ACL seguirá configurada en el enrutador Para eliminar la ACL del router, use el comando de configuración global no access-list .

![[Pasted image 20260406205253.png]]


si suponemos que solo PC1 esta permitido salir a internet para habilitar esta opcion o directiva, se podrian aplicar una ACE ACL estandar saliente en S0/1/0.

![[Pasted image 20260406205650.png]]

como se ve el comando show acces-list no muestra las notas o instrucciones de remark. se muestra en el archivo de configuracion en ejecucion. aunque el remark no es necesario o obligatorio para poder habilitar un ACL es considerada un buena practica.

Otro escenario seria que la directiva quiere que la red LAN 2 tambein deben ser permitidos a internet. Para habilitar esta directiva, se tiene que agregar una segunda ACE al ACL 10.

![[Pasted image 20260406210059.png]]

Aplicacion la ACL 10 a la interfaz de salida la cual en este caso seria la interfaz Serial0/1/0

![[Pasted image 20260406210229.png]]

usamos el comando show running-config para revisar las ACL y las filtramos para que nos la muestre de la siguiente manera.

![[Pasted image 20260406212734.png]]

de igual manera para verificar si una interfaz tiene una ACL aplciada podemos emplear el comando Show ip interface de a siguiente manera.

![[Pasted image 20260406213707.png]]


#### Aplicacion de ACL estandar nombrada IPv4

![[Pasted image 20260406225637.png]]


En este caso PC1 esta permitido salir a internet, para lograr habilitar esta ACE en la ACL que llamaremos como PERMIT-ACCESS la cual se aplicaria en la S0/1/0

![[Pasted image 20260406232525.png]]

en este caso solo se permite el trafico de salida al host que termina en .10 solo ese host de toda la lan1 y como nueva directiva o ACE permitiremos toda la red de lan2 de la sigueinte manera.

![[Pasted image 20260406232756.png]]

![[Pasted image 20260406232811.png]]![[Pasted image 20260406232831.png]]


![[Pasted image 20260406232839.png]]
