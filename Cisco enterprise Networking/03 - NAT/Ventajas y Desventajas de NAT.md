---
tipo: [[NAT]]
tema: Ventajas y Desventajas de NAT
estado: Completado
region: [[Parietal]]
---
# [[NAT Pros and Cons]]

## Ventajas de NAT
[[NAT]] proporciona beneficios significativos para la arquitectura de red:

*   **Conservación de direcciones:** Permite la multiplexación de aplicaciones a nivel de puerto (PAT). Los hosts internos comparten una única [[IPv4]] pública para comunicaciones externas, reduciendo el consumo de direcciones legales.
*   **Flexibilidad:** Facilita el uso de conjuntos de respaldo y equilibrio de carga para asegurar conexiones confiables a la red pública.
*   **Coherencia interna:** Permite mantener el esquema de direcciones privadas existente sin tener que redireccionar toda la red si se cambia de [[ISP]], evitando costos operativos altos.
*   **Privacidad:** Al usar direcciones [[RFC 1918]], oculta los dispositivos internos de las redes externas. *Nota: La mayoría de los expertos coinciden en que esto no sustituye a un [[Firewall]].*

## Desventajas de NAT
Como el dispositivo [[NAT]] interviene en la comunicación, se generan diversos problemas técnicos detallados a continuación:

| Problema                  | Impacto Técnico                                                                                            |                                                                                  |
| :------------------------ | :--------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- |
| **Rendimiento**           | Aumenta el retraso por recálculo de [[Checksum]] y modificación de encabezados ([[TCP]]/[[UDP]]/[[IPv4]]). |                                                                                  |
| **[[Carrier Grade NAT     | CGN]]**                                                                                                    | Traducción en dos capas (ISP a Cliente), complicando la infraestructura.         |
| **[[End-to-End Principle  | Pérdida de extremo a extremo]]**                                                                           | Fallan firmas digitales y protocolos que requieren la [[IP]] original de origen. |
| **Troubleshooting**       | Dificulta el seguimiento de paquetes a través de múltiples saltos de [[NAT]].                              |                                                                                  |
| **[[IPsec]]**             | Modifica valores de encabezado, causando fallos de integridad.                                             |                                                                                  |
| **Protocolos sin estado** | Interrupción de servicios [[UDP]] o conexiones [[TCP]] iniciadas desde el exterior.                        |                                                                                  |

> Nota: Algunos protocolos pueden acomodar una instancia de [[NAT]] (como [[FTP]] en modo pasivo), pero fallan cuando [[NAT]] separa ambos sistemas de [[Internet]].