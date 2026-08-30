---
tipo: [[OSPF]]
tema: Propagación de Ruta Predeterminada
estado: Completado
region: [[Parietal]]
---
# [[Default Route Propagation]]
Cuando los usuarios de una red deberán enviar paquetes fuera de las redes que no sean [[OSPF]] (como Internet), se necesita una ruta estática. El router ubicado entre el dominio de enrutamiento [[OSPF]] y la red externa se denomina [[ASBR]] (Router de frontera de sistema autónomo).

![[Pasted image 20260318193646.png]]

## Configuración en el [[ASBR]]
Para propagar una ruta predeterminada, el router de borde (como R2 en el ejemplo) debe configurarse con los siguientes componentes:

| Comando | Función |
| :--- | :--- |
| `ip route 0.0.0.0 0.0.0.0 [next-hop \| exit-intf]` | Crea la ruta estática predeterminada. |
| `default-information originate` | Ordena al router propagar la ruta estática en las actualizaciones [[OSPF]]. |
> Nota: En el ejemplo se utiliza una interfaz loopback con la dirección IPv4 64.100.0.1 para simular la conexión con el proveedor de servicios. Al simular una conexión a Internet, no hay dirección IP de salto siguiente, por lo que se utiliza el argumento `exit-intf`.

## Ejemplo de Configuración
```bash
R2(config)# interface lo1
R2(config-if)# ip address 64.100.0.1 255.255.255.252
R2(config-if)# exit
R2(config)# ip route 0.0.0.0 0.0.0.0 loopback 1
%Default route without gateway, if not a point-to-point interface, may impact performance
R2(config)# router ospf 10
R2(config-router)# default-information originate
R2(config-router)# end
R2#