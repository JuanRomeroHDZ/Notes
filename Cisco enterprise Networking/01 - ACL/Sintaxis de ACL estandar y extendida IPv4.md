---
tipo: [[Access Control List]]
tema: Sintaxis de ACL estandar y extendida IPv4
estado: Completado
region: [[Parietal]]
---
# [[Standard ACL Syntax]]
## [[Numbered Standard ACL]]
En general, para crear una [[Standard ACL|ACL estándar numerada]] se emplea el siguiente comando:
`Router(config)# access-list access-list-number {deny | permit | remark text} source [source-wildcard] [log]`
![[Pasted image 20260406203755.png]]
![[Pasted image 20260406203819.png]]

## [[Named Standard ACL]]
En cuanto a la función, solo mejora la versatilidad ya que es más fácil identificarla de esta manera.
![[Pasted image 20260406204321.png]]
![[Pasted image 20260406204521.png]]

# [[Standard ACL Application]]
Una vez se tenga la [[Access Control List|ACL]] configurada correctamente, se emplearía el siguiente comando dentro de la configuración de una [[Interface]] previamente seleccionada:
![[Pasted image 20260406204813.png]]

## Eliminación de ACL
Para eliminar una [[Access Control List|ACL]] de una [[Interface]], primero introduzca el comando de configuración `no ip access-group interface`. Sin embargo, la [[Access Control List|ACL]] seguirá configurada en el [[Router]]. Para eliminar la [[Access Control List|ACL]] del router, use el comando de configuración global `no access-list`.
![[Pasted image 20260406205253.png]]

## Escenario: PC1 a Internet
Si suponemos que solo PC1 tiene permitido salir a internet, para habilitar esta opción o directiva se podría aplicar una [[ACE]] de una [[Standard ACL|ACL estándar]] saliente en S0/1/0.
![[Pasted image 20260406205650.png]]
Como se ve, el comando `show access-list` no muestra las notas o instrucciones de `remark`. Se muestra en el archivo de configuración en ejecución. Aunque el `remark` no es necesario u obligatorio para poder habilitar una [[Access Control List|ACL]], es considerada una buena práctica.

## Escenario: LAN2 a Internet
Otro escenario sería que la red LAN2 también debe ser permitida a internet. Para habilitar esta directiva, se tiene que agregar una segunda [[ACE]] a la [[Access Control List|ACL]] 10.
![[Pasted image 20260406210059.png]]
Aplicación de la [[Access Control List|ACL]] 10 a la interfaz de salida, la cual en este caso sería la interfaz Serial0/1/0:
![[Pasted image 20260406210229.png]]
Usamos el comando `show running-config` para revisar las [[Access Control List|ACL]] y las filtramos para que nos las muestre de la siguiente manera:
![[Pasted image 20260406212734.png]]
De igual manera, para verificar si una [[Interface]] tiene una [[Access Control List|ACL]] aplicada podemos emplear el comando `show ip interface` de la siguiente manera:
![[Pasted image 20260406213707.png]]

# [[Named Standard ACL Application]]
![[Pasted image 20260406225637.png]]
En este caso, PC1 tiene permitido salir a internet. Para habilitar esta [[ACE]] en la [[Access Control List|ACL]] que llamaremos "PERMIT-ACCESS", la cual se aplicaría en la S0/1/0:
![[Pasted image 20260406232525.png]]
En este caso solo se permite el tráfico de salida al host que termina en .10 (solo ese host de toda la LAN1) y, como nueva directiva o [[ACE]], permitiremos toda la red de LAN2 de la siguiente manera:
![[Pasted image 20260406232756.png]]
![[Pasted image 20260406232811.png]]
![[Pasted image 20260406232831.png]]
![[Pasted image 20260406232839.png]]