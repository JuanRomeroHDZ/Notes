
usualmente en las ACL con muchas ACEs es difícil mantener un orden en las cuales pueden llegar a generar errores, de tal manera que cuando se necesita editar algún parámetro de las mismas. se puede hacer de 2 maneras las cuales son

- Editor de texto
básicamente se basa en copiar la ACL que esta errónea en producción o rediseñarla. de igual manera se recomienda hacerla inicialmente en un editor de texto como el bloc de notas para solo copiar y pegar lo cual evitaría errores.
ejemplos:

![[Pasted image 20260407003351.png]]

corrección

![[Pasted image 20260407003408.png]]


- Números de Secuencia

Una ACE de un ACL también se puede eliminar o agregar utilizando los números de secuencia ACL. Los números de secuencia se asignan automáticamente cuando se introduce una ACE. Estos números se enumeran en el comando show access-lists . El comando show running-config no muestra números de secuencia.

En el ejemplo anterior, el ACE incorrecto para ACL 1 esta utilizando el número de secuencia 10, como se muestra en el ejemplo.

![[Pasted image 20260407003624.png]]
![[Pasted image 20260407003710.png]]