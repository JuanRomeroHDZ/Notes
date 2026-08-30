---
tipo: [[Access Control List]]
tema: Proteccion de puertos VTY con ACL
estado: Completado
region: [[Parietal]]
---
# [[VTY ACL Protection]]
En las [[Access Control List|ACL]] normalmente se filtran las [[Access Control List|ACL]] mediante el trafico de entrada o de salida en las interfaces, pero las [[Access Control List|ACL]] también pueden proteger el acceso remoto a un equipo mediante las [[VTY lines|líneas VTY]]. Para poder aplicar una [[Access Control List|ACL]] en una [[VTY lines|líneas VTY]] se hace de la siguiente manera.
![[Pasted image 20260408162852.png]]
En estos casos la palabra clave [[Inbound ACL|in]] es la mas empleada para el trafico [[VTY lines|VTY]] entrante, ya que el [[Outbound ACL|out]] filtra el trafico saliente en las [[VTY lines|vty]] y rara vez se aplica.

Las [[Numbered ACL|ACL numeras]] y [[Named ACL|nombradas]] se pueden aplicar en las [[VTY lines|líneas VTY]].
Un ejemplo para aplicar un [[Access Control List|ACL]] en las [[VTY lines|líneas VTY]] seria de la siguiente manera y escenario, el cuales escenario es que se tiene que configurar el [[Telnet]] para que solo el admin tenga acceso al [[Telnet]] del equipo.
![[Pasted image 20260408165124.png]]
En el caso del [[SSH]] se haria de la siguiente manera.
![[Pasted image 20260408165150.png]]