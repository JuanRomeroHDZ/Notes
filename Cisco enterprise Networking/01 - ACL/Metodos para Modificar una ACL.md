---
tipo: [[ACL Modification]]
tema: Metodos para Modificar una ACL
estado: Completado
region: [[Parietal]]
---
# [[ACL Modification]]
Usualmente en las [[Access Control List|ACL]] con muchas [[Access Control Entry|ACE]] es difícil mantener un orden en las cuales pueden llegar a generar errores, de tal manera que cuando se necesita editar algún parámetro de las mismas, se puede hacer de 2 maneras:
## [[Text Editor]]
Básicamente se basa en copiar la [[Access Control List|ACL]] que esta errónea en producción o rediseñarla. De igual manera se recomienda hacerla inicialmente en un [[Text Editor]] como el bloc de notas para solo copiar y pegar lo cual evitaría errores.
![[Pasted image 20260407003351.png]]
Corrección:
![[Pasted image 20260407003408.png]]
## [[Sequence Numbers]]
Una [[Access Control Entry|ACE]] de una [[Access Control List|ACL]] también se puede eliminar o agregar utilizando los [[Sequence Numbers|números de secuencia]] [[Access Control List|ACL]]. Los [[Sequence Numbers|números de secuencia]] se asignan automáticamente cuando se introduce una [[Access Control Entry|ACE]]. Estos números se enumeran en el comando `show access-lists`. El comando `show running-config` no muestra [[Sequence Numbers|números de secuencia]].
En el ejemplo anterior, el [[Access Control Entry|ACE]] incorrecto para [[Access Control List|ACL]] 1 esta utilizando el número de secuencia 10, como se muestra en el ejemplo.
![[Pasted image 20260407003624.png]]
![[Pasted image 20260407003710.png]]
