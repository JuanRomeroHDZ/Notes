---
tipo: [[Dynamic NAT]]
tema: Configuración NAT Dinámica
estado: Completado
region: [[Parietal]]
---
# [[Dynamic NAT]]
El [[Dynamic NAT]] consiste en la misma función o una función similar al [[DHCP]], ya que su misión es proporcionar direcciones traducidas para que los dispositivos en la red puedan acceder a la red externa o [[Internet]]. Funciona con un [[NAT Pool|pool de direcciones]] al igual que el [[DHCP]] y de esa manera las sigue entregando. Cuando no hay disponibles para otro dispositivo, se tiene que esperar hasta que una se desocupe.

## Configurar NAT dinámica
Como tal, el [[Dynamic NAT]] es sencillo de configurar siguiendo estos pasos:

1. ![[Pasted image 20260428210042.png]]
2. ![[Pasted image 20260428210108.png]]
3. ![[Pasted image 20260428210124.png]]
4. ![[Pasted image 20260428210135.png]]
5. ![[Pasted image 20260428210150.png]]

## Análisis de [[Dynamic NAT]]
### Interior a exterior
![[Pasted image 20260428210837.png]]
![[Pasted image 20260428210901.png]]

### Exterior a interior
![[Pasted image 20260428211532.png]]
![[Pasted image 20260428211600.png]]

## Verificar [[Dynamic NAT]]
Para ver la salida de las traducciones empleamos el comando `show ip nat translations`. Esta nos mostrará las traducciones que se han configurado.

![[Pasted image 20260428212510.png]]
![[Pasted image 20260428212539.png]]
![[Pasted image 20260428212706.png]]
![[Pasted image 20260428212732.png]]
![[Pasted image 20260428212750.png]]
![[Pasted image 20260428213008.png]]