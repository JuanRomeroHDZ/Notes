---
tipo: [[IPv4 Addressing]]
tema: Espacio de Direcciones IPv4 Privadas
estado: Completado
region: [[Parietal]]
---
# [[Private IPv4 Address Space]]
![[Pasted image 20260411221905.png]]
Estas [[IPv4 Private Address|direcciones privadas]] se utilizan dentro de una organización o un sitio para permitir que los dispositivos se comuniquen localmente. Sin embargo, debido a que estas direcciones no identifican a una sola empresa u organización, las [[IPv4 Private Address|direcciones IPv4 privadas]] no se pueden enrutar a través de [[Internet]]. Para permitir que un dispositivo con una [[IPv4 Private Address|dirección IPv4 privada]] acceda a recursos y dispositivos fuera de la red local, primero se debe traducir la dirección privada a una [[Public IPv4 Address|dirección pública]].

[[NAT]] proporciona la traducción de direcciones privadas a [[Public IPv4 Address|direcciones públicas]], como se muestra en la figura. Esto permite que un dispositivo con una [[IPv4 Private Address|dirección IPv4 privada]] acceda a recursos fuera de su red privada, como los que se encuentran en [[Internet]]. [[NAT]], combinado con [[IPv4 Private Address|direcciones IPv4 privadas]], ha sido el método principal para preservar las [[Public IPv4 Address|direcciones IPv4 públicas]]. Se puede compartir una única [[Public IPv4 Address|dirección IPv4 pública]] entre cientos o incluso miles de dispositivos, cada uno configurado con una [[IPv4 Private Address|dirección IPv4 privada]] exclusiva.
![[Pasted image 20260411222049.png]]
