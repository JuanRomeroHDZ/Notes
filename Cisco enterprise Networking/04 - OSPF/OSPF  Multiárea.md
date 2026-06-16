

El OSPF Multiárea consiste en una serie de redes o de áreas mas pequeñas debido que si la red de routers o el área fuera muy grande la tabla de [[LSDB]] seria muy grande por lo tanto no calcularía bien el SPF o no le ejecutaría en todas debido que el calculo de SPF , Actualizar el  LSDB , y El árbol de enrutamiento exige un gran costo en el Procesador. Por lo tanto su rendimiento se vería perjudicado dejando de lado varios routers fuera de la tabla de enrutamiento. 
Ese es el problema que busca Solucionar el OSPF Multiárea busca crear varias áreas pequeñas y unirlas en una por lo tanto así una área contendría los ABR o los routers fronterizos los cuales se encargarían de hacer su propia tabla de LSDB de cada área y mandarlo a la área líder la cual maneja los ABR , por lo tano si un área fallan las demás no se ven perjudicadas y no re ejecutarían el SPF y ni mandar LSA solamente se comunicarían con el ABR afectado.

![[Pasted image 20260207222854.png]]