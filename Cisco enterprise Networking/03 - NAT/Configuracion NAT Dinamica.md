---
tipo: [[Dynamic NAT]]
tema: Configuración NAT Dinamica
estado: Completado
region: [[Parietal]]
---
# [[Dynamic NAT]]
La [[Dynamic NAT]] es un mecanismo de traducción de direcciones que utiliza un grupo (pool) de direcciones [[IP]] públicas para asignarlas dinámicamente a los hosts de la red interna. A diferencia de la [[Static NAT]] (que es uno a uno), la [[Dynamic NAT]] permite mapear muchas direcciones privadas a un grupo limitado de direcciones públicas de forma automatizada.

## Flujo de trabajo
1. El host interno envía un paquete hacia el exterior.
2. El [[Router]] verifica si existe una coincidencia en la [[Access Control List|ACL]].
3. Si coincide, el [[Router]] asigna una dirección pública disponible del [[NAT Pool]] a la [[IP]] privada del host.
4. El [[Router]] crea una entrada en la tabla de traducción y reenvía el paquete.

## Pasos de configuración
### 1. Definir interfaces
Se debe indicar qué interfaz es interna y cuál es externa.
`Router(config-if)# ip nat inside`
`Router(config-if)# ip nat outside`

### 2. Crear [[Access Control List|ACL]]
Define el tráfico permitido para ser traducido (el tráfico de origen).
`Router(config)# access-list [numero] permit [red_origen] [wildcard]`

### 3. Crear [[NAT Pool]]
Define el rango de direcciones [[IP]] públicas disponibles.
`Router(config)# ip nat pool [nombre_pool] [ip_inicial] [ip_final] netmask [mascara]`

### 4. Mapear [[Access Control List|ACL]] a [[NAT Pool]]
Vincula el tráfico identificado con el pool de direcciones.
`Router(config)# ip nat inside source list [numero_acl] pool [nombre_pool]`

## Verificación
Utiliza los siguientes comandos para confirmar que las traducciones están ocurriendo correctamente:

| Comando | Descripción |
| :--- | :--- |
| `show ip nat translations` | Muestra las traducciones activas. |
| `show ip nat statistics` | Muestra información sobre el funcionamiento y uso de los pools. |
| `clear ip nat translation *` | Borra las traducciones dinámicas de la tabla. |

> Nota: Si el [[NAT Pool]] se agota, los hosts internos no podrán acceder a Internet hasta que una traducción previa expire o sea liberada.