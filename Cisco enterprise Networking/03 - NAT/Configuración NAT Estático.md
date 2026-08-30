---
tipo: [[Static NAT]]
tema: Configuración NAT Estático
estado: Completado
region: [[Parietal]]
---
# [[Static NAT]]
Una configuración [[Static NAT]] se basa casi únicamente en dos pasos.

## Paso 1: Asignación de direcciones
Consiste en hacer la asignación entre la [[Inside Local Address|dirección local interna]] y las [[Inside Global Address|direcciones globales internas]].
![[Pasted image 20260412193636.png]]

## Paso 2: Asignación en interfaces
Las interfaces que participan en la traducción se configuran como interna o externa con respecto a [[NAT]]. En el ejemplo, la interfaz R2 Serial 0/1/0 es una [[NAT Inside Interface|interfaz interna]] y la Serial 0/1/1 es una [[NAT Outside Interface|interfaz externa]].
![[Pasted image 20260412193850.png]]

Con esta configuración, los paquetes que llegan a la [[NAT Inside Interface|interfaz interna]] de R2 (Serial 0/1/0) desde la [[Inside Local Address|dirección IPv4 local interna]] configurada (192.168.10.254) se traducen y luego se reenvían hacia la red externa. Los paquetes que llegan a la [[NAT Outside Interface|interfaz externa]] de R2 (Serial 0/1/1), que se dirigen a la [[Inside Global Address|dirección IPv4 global interna]] configurada (209.165.201.5), se traducen a la [[Inside Local Address|dirección local interna]] (192.168.10.254) y luego se envían dentro de la red.

## Verificación
Para verificar empleamos el comando `show ip nat translations`, lo cual nos mostrará algo como lo siguiente:
![[Pasted image 20260412195319.png]]

Otros comandos útiles:

| Comando | Descripción |
| :--- | :--- |
| `show ip nat statistics` | Muestra información sobre el número total de traducciones activas, los parámetros de configuración de NAT, el número de direcciones en el grupo y el número de direcciones asignadas. |
| `clear ip nat statistics` | Borra las estadísticas de cualquier traducción anterior antes de realizar la prueba. |

Para verificar que la traducción [[NAT]] está funcionando, es mejor borrar las estadísticas utilizando `clear ip nat statistics` antes de realizar la prueba.
![[Pasted image 20260412195440.png]]
![[Pasted image 20260412195516.png]]