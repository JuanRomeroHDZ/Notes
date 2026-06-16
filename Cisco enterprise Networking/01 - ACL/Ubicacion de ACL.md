
Las ACL por regla general se aplican donde tengan mejor rendimiento e impacto para evitar errores.

en general las ACL estandar se deben colocar lo mas cerca al destino el cual se desea bloquear o permitir el trafico. ya que si como las estandar solo estan en capa 3 con IP si lo pones lo mas cercano al origen bloquearias trafico que no solo va al destino que tu quieres bloquear.

En las ACL extendidas pasa lo contrario , estas deben de ir por lo general lo mas cercano al origen para poder filtrar por protocolos entre otros.


![[Pasted image 20260406144431.png]]

![[Pasted image 20260406144508.png]]


