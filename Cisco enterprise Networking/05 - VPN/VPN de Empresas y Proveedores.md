---
tipo: [[VPN]]
tema: VPN de Empresas y Proveedores
estado: Completado
region: [[Parietal]]
---
# [[Enterprise and Provider VPNs|VPN de Empresas y Proveedores]]
Las redes privadas virtuales se pueden clasificar según su propósito, el entorno en el que se despliegan y la entidad responsable de su gestión y mantenimiento.

## VPNs Empresariales
Las VPNs empresariales usualmente se usan para proteger el tráfico interno que tiene la intención de salir al exterior de la red de la empresa. Esto ayuda notablemente a proteger los datos mediante el uso de protocolos seguros para mantener cifrados todos los paquetes. Por lo general, estas conexiones son administradas de forma directa por los mismos empleados del departamento de TI de la empresa, casi nunca por un tercero.

## VPNs de Proveedor de Servicios
Las VPNs que son administradas por proveedores de servicios se crean y se gestionan a través de la infraestructura de red del propio proveedor, no desde la red local del usuario. Estas soluciones permiten interconectar de forma segura múltiples sitios geográficos de una organización.

| Tipo de VPN | Entorno y Administración | Tecnologías de Enlace | Objetivo Principal |
| :--- | :--- | :--- | :--- |
| [[Enterprise VPN\|Empresariales]] | Administradas internamente por los mismos empleados de la empresa sobre la red local. | [[IPsec]] y [[SSL]] | Proteger y cifrar el tráfico interno que se dirige hacia el exterior de la infraestructura corporativa. |
| [[Service Provider VPN\|Proveedor de Servicios]] | Administradas por terceros a través de la infraestructura de red del proveedor de servicios. | [[MPLS]] (Opera en [[Layer 2\|Capa 2]] y [[Layer 3\|Capa 3]]) | Crear canales de transporte totalmente seguros e independientes entre los diferentes sitios del cliente. |

![[Pasted image 20260513194745.png]]