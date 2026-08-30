---
tipo: [[OSPF]]
tema: Sincronización de Bases de Datos OSPF
estado: Completado
region: [[Parietal]]
---
# [[OSPF Database Synchronization]]
Tras el proceso Two-Way, los routers ingresan al estado de sincronización de su [[Link State Database|LSDB]]. Mientras que el primer paquete Hello se emplea para establecer la adyacencia, los otros cuatro tipos de paquetes [[OSPF]] se utilizan durante el proceso de intercambio y sincronización, el cual consta de tres pasos.

## [[Exstart State]]
En este estado, los routers deciden quién enviará los paquetes [[Database Description|DBD]] primero. Esta elección se basa en el [[Router ID]]: el dispositivo con el valor más alto toma la iniciativa.

![[Pasted image 20260219233844.png]]

## [[Exchange State]]
El intercambio de paquetes [[Database Description|DBD]] proporciona información sobre las entradas de [[LSA]] presentes en la [[Link State Database|LSDB]]. 

| Elementos Incluidos en el Encabezado LSA     |
| :------------------------------------------- |
| Tipo de estado del enlace.                   |
| Dirección del router que realiza el anuncio. |
| Costo del enlace.                            |
| Número de secuencia.                         |
El router utiliza el número de secuencia para determinar la vigencia de la información del estado de enlace.

![[Pasted image 20260219234235.png]]

## [[Loading State]]
En esta fase, el router compara la información recibida con su propia [[Link State Database|LSDB]]. Si el paquete [[Database Description|DBD]] contiene una entrada de estado de enlace más actual, se genera un [[Link-State Request|LSR]] y el proceso transita al estado de Loading.

![[Pasted image 20260219234454.png]]