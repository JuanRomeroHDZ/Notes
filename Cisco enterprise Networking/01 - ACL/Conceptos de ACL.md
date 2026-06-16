

### Que es una ACL 

 los enrutadores son los que toman las decisiones de enrutamiento basadas en la información del encabezado del paquete. así el trafico que entra a una interfaz de enrutador se enruta únicamente en función de la información dentro de la tabla de enrutamiento.
 el router compara la direccion ip de destino con las rutas de la tabla de enrutamiento para econtrar la mejor coincidencia y , a continuacion reenvia el paquete segun la mejro ruta de coincidencia. exactamente ese mismo proceso se puede utilizar paraf filtratr el trafico mediante una lista de control de acceso (ACL) 
las ACL funcionn filtrando paquetes en las capas 3(red) y 4(transporte) del modelo osi
ejemplos de tareas que hace una ACL :

![[Pasted image 20260406122252.png]]

![[Pasted image 20260406122545.png]]



### Tipos de ACL

Los router cisco admiten dos tipos de ACL

aun que existen varios tipos de acl incluso para vlan directamente en los switches de capa 3 en los routers cisco se admiten las siguentes.

- ACL estandar
Las ACL estandar solo filtarn en la capa 3 utilizando unicamente la direccion IPv4 de origen.
- ACL extendida
Las ACL extendidas filtran en la capa 3 mediante la direccion IPv4 de origen o destino, tambien puede filtrar en la capa 4 mediante TCP, puertos UDP e informacion de tipo de protocolo opcional para un controlo mas exacto en las redes
- ACL numeradas y nombradas
las acl numeradas y nombradas como tal no son 2 ACLs nuevas si no que son 2 terminos al crear una acl ya que que puedas crear una acl estandar o extendida con un numero (ACL numerada) en vez e un nombre por ejemplo "ACL 10,20 o 30" , y  asu vez puedes crear una ACL con un nombre en especifico (ACL nombrada) por ejemplo "Bloquear youtube" y de esa manera no pones un numero como las numeradas

![[Pasted image 20260406124254.png]]