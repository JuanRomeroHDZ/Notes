

En el protocolo ospfs se necesita el costo por salto pero el protocolo de enrutamiento utiliza una métrica para lograr determinar la mejor ruta de un paquete a través de una red. una métrica avisa sobre la sobrecarga  que se requiere para enviar los paquetes en una interfaz predeterminada.
cuando el costo es menor, la ruta es mejor que una con un costo mayor.

En el caso de cisco de un interfaz es inversamente proporcional al ancho de banda de la interfaz. por lo tanto en cuanto mayor sea el ancho de banda menor ser ale costo.
la formula siguiente es una métrica para calcularlo , tomando en cuenta que el ancho de banda predeterminado es de 10^8 (100,000,000).

![[Pasted image 20260310212132.png]]

![[Pasted image 20260310212242.png]]

en el caso de los costos cuando el costo no es un numero entero ósea el resultado es un decimal, se redondea al numero entero mas cercano como le ejemplo de la tabla que se muestra un resultado de 0.01 se redondea a 1 ya que es el mas cercano.

para el calculo el cambiar el costo de referencia de ancho de banda como tal no afecta a la velocidad de la interfaz si no que afecta únicamente el costo de el ancho de banda, dejándonos una mejor métrica de costos y asu vez dándonos una mejor ruta para el ospf el comando que se empleara para cambiar el ancho de banda de referencia es:
"```Router(config-router)# auto-cost reference-bandwidth Mbps"

tomando en cuenta que en el caso de cambiar el costo de ancho de banda de referencia se tendra que introducir el valor en megabits por ejemplo:

para uan interfaz de 10 gigabit el comando seria:

```
Router(config-router)# auto-cost reference-bandwidth 10000
```

así declaramos la velocidad del ancho de banda, un dato a tomar en cuenta es que se tiene que aplicar a todos los routers de la red ospf

![[Pasted image 20260310214043.png]]


### Costos acumulados de OSPF

El cosot acumulado es la suma del costo de ancho de banda de referencia y el costo de el loopback por lo tanto el loopback pro default es de 1 y si el costo entre routers es de 10 entonces seria un costo total de 11.

![[Pasted image 20260310215255.png]]

![[Pasted image 20260310215809.png]]

**Nota:** Aunque utilizar el **ip ospf cost** comando es el método recomendado para manipular los valores de costo OSPF, un administrador también podría hacerlo mediante el comando interface configuration **bandwidth** _kbps_ Sin embargo, eso solo funcionaría si todos los routers son routers Cisco.

![[Pasted image 20260310215907.png]]


