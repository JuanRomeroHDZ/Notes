---
tipo: [[PAT]]
tema: Port Address Translation
estado: Completado
region: [[Parietal]]
---
# [[Port Address Translation|PAT]]
La [[Port Address Translation|PAT]] (también conocida como [[NAT Overload|NAT con sobrecarga]]) es el método de configuración más común en empresas y hogares.

## Funcionamiento
A diferencia de la [[NAT]], que mapea direcciones privadas a públicas, [[PAT]] realiza la traducción basándose en el tipo de petición de protocolos [[TCP]], [[UDP]], [[ICMP]], etc., asignando números de puerto a las direcciones de salida.

Esto ayuda a gestionar la recepción de paquetes de regreso al [[Router]], asegurando que se envíen con el número de puerto de origen correcto. [[PAT]] garantiza que no se asigne el mismo número de puerto a una misma dirección [[IP]].
![[Pasted image 20260412153407.png]]

## [[Next Available Port]] Logic
[[PAT]] intenta conservar el puerto de origen inicial. Sin embargo, si el puerto original ya está en uso, [[PAT]] asigna el primer número de puerto disponible dentro de los rangos apropiados:
* 0 - 511
* 512 - 1,023
* 1,024 - 65,535

Cuando no hay más puertos disponibles y existe más de una dirección externa en el conjunto, [[PAT]] avanza a la siguiente dirección para intentar asignar el puerto original. Este proceso continúa hasta agotar todos los puertos y direcciones [[IPv4]] externas.

## Diferencias entre [[NAT]] y [[PAT]]
![[Pasted image 20260412183540.png]]
![[Pasted image 20260412183650.png]]
![[Pasted image 20260412183704.png]]