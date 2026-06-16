
despues de l proceso two-way los routers ingresan a un estado de sicronizacion de bases de datos , mientras que el primer paquete hello se empleo para crear la adyacencia los otros 4 tipos de paqeutes se usan durante el proceso de intercambio y sincronisacion de LSDB, este sule ser un proceso de 3 pasos .

- Decidir el primer router.
- Intercambio de DBD
- Enviar Un LSR


#### Decidir el primer router

En el estado de Exstar, los dos routers deciden entre si quien enviara los paquedes DBD primero, Eso se decide con el que tenga el router id mas alto. El que se mas alto mandara el paquete primero, y despues el otro.

![[Pasted image 20260219233844.png]]


#### Intercambio DBD 

Un paquete DBD incluye la informacion acerca de la entrada de LSA que aparace en la LSDB del router, las entradas puedes hacer el enlace a una red o cada encabezado de entrada LSA incluye informacion acerca del tipo de estado del enlace, ladireccion de router que realiza el anuncio , el costo del enlance, numero de secuencia. El router usa el numero de secuencia para poder determinar que tan nueva es la informacion del estado de enlace recibida.

![[Pasted image 20260219234235.png]]


####  Enviar un LSR

en este caso el R1 comapra la informacion que recibio con la que tenia en su propia LSDB , en caso de que el paquete DBD dtenga un entrada de estado de enlace mas actual , el router pasara a estado de Loading.

![[Pasted image 20260219234454.png]]