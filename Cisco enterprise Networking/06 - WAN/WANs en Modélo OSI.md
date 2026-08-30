---
tipo: [[WAN]]
tema: WANs en el Modelo OSI
estado: Completado
region: [[Parietal]]
---
# [[WANs in the OSI Model|WANs en el Modelo OSI]]
La mayoría de las WAN funcionan en dos capas principales del [[Modelo OSI]], y muchos de sus servicios también se segmentan dentro de estas funciones.

## Protocolos de Capa 1
Los protocolos de la [[Capa 1]] (Capa Física) describen los componentes eléctricos, mecánicos y operativos necesarios para transmitir bits a través de una WAN. 

Por ejemplo, los proveedores de servicios suelen utilizar medios de fibra óptica de gran ancho de banda para recorrer largas distancias utilizando los siguientes estándares de protocolo óptico:
 
| Estándar de Capa 1 | Nombre Completo                                       | Descripción Operativa                                                                               |
| :----------------- | :---------------------------------------------------- | :-------------------------------------------------------------------------------------------------- |
| **[[SDH]]**        | Jerarquía Digital Sincrónica                          | Estándar global sincrónico para el transporte de datos en fibra óptica.                             |
| **[[SONET]]**      | Red Óptica Síncrona                                   | Protocolo sincrónico de transporte óptico utilizado principalmente en América del Norte.            |
| **[[DWDM]]**       | Multiplexación por División de Longitud de Onda Densa | Tecnología que aumenta la capacidad de transmisión de SDH y SONET multiplexando frecuencias de luz. |

## Protocolos de Capa 2
Los protocolos de la [[Capa 2]] (Capa de Enlace de Datos) definen cómo se encapsularán los datos en una trama para su transporte hacia los destinos remotos. Varios protocolos han evolucionado a lo largo de los años de acuerdo con las necesidades de la infraestructura:

| Protocolo de Capa 2 | Tipo / Estado de la Tecnología |
| :--- | :--- |
| **Banda Ancha** | Implementaciones modernas a través de [[DSL]] y Cable módem. |
| **Inalámbrico** | Soluciones WAN por radiofrecuencia o conexiones satelitales. |
| **[[Metro Ethernet]]** | También conocido como Ethernet WAN; es el estándar de alto rendimiento actual. |
| **[[MPLS]]** | Multiprotocol Label Switching; enrutamiento eficiente basado en etiquetas. |
| **[[PPP]]** | Point-to-Point Protocol; encapsulación dedicada síncrona/asíncrona (menos usado). |
| **[[HDLC]]** | High-Level Data Link Control; control de enlace de datos de alto nivel (menos usado). |
| **[[Frame Relay]]** | Tecnología de conmutación de paquetes por circuitos virtuales (heredado/obsoleto). |
| **[[ATM]]** | Asynchronous Transfer Mode; conmutación orientada a celdas de tamaño fijo (heredado/obsoleto). |