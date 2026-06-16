

En las ACL normalmente se filtran las ACL mediante el trafico de entrada o de salida en las interfaces , pero las ACL también pueden proteger el acceso remoto a un equipo mediante las líneas VTY.

para poder aplicar una ACL en una líneas VTY se hace de la siguiente manera.

![[Pasted image 20260408162852.png]]

en estos casos la palabra clave 'in' es la mas empleada para el trafico VTY entrante. ya que el 'out' filtra el trafico saliente en las vty y rara vez se aplica.
Las ACL numeras y nombradas se pueden aplicar en las líneas VTY.

un ejemplo para aplicar un ACL en las líneas VTY. seria de la siguiente manera y escenario. el cuales escenario es que se tiene que configurar el telnet para que solo el admin tenga acceso al telnet del equipo.

![[Pasted image 20260408165124.png]]


En el caso de SSH se haria de la siguiente manera.

![[Pasted image 20260408165150.png]]