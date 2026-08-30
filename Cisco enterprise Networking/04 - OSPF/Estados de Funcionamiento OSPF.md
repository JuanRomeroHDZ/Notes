---
tipo: [[OSPF]]
tema: Estados de Funcionamiento OSPF
estado: Completado
region: [[Parietal]]
---
# [[OSPF Operational States]]
Cuando se habilitan nuevos [[Router|routers]] en una red [[OSPF]], el proceso de convergencia sigue una secuencia estricta para establecer adyacencias.

## Establecimiento de Adyacencias
Al habilitar [[OSPF]] en una interfaz, el router busca vecinos enviando paquetes [[OSPF Hello Packet|Hello]] vía [[Multicast]] (dirección `224.0.0.5`). Solo los routers con [[OSPFv2]] procesan estos paquetes. La adyacencia inicia al capturar el [[Router ID]] del paquete [[Hello]].

<br>

| Estado | Acción |
| :--- | :--- |
| **Down** | El protocolo [[OSPF]] está deshabilitado; no se reciben paquetes [[Hello]]. |
| **Init** | El router ha enviado un paquete [[Hello]] y está esperando respuesta. |
| **Two-Way** | Comunicación bidireccional; ambos routers se reconocen en la lista de vecinos. |

<br>
## Ciclo de vida de estados

### 1. [[Down State]] a [[Init State]]
Al habilitar la interfaz, el [[OSPFv2]] pasa a estado `Init`. El router comienza a enviar paquetes [[Hello]] por todas las interfaces configuradas para descubrir vecinos.
![[Pasted image 20260219232006.png]]

### 2. [[Init State]]
El vecino (R2) recibe el [[Hello]] de R1, agrega el [[Router ID]] de R1 a su lista y responde con un paquete [[Hello]] que contiene su propio [[Router ID]] y el de R1.
![[Pasted image 20260219232338.png]]

### 3. [[Two-Way State]]
R1 recibe el [[Hello]] de R2. Al ver su propio [[Router ID]] en la lista de vecinos del paquete recibido, la comunicación se confirma como bidireccional. La acción posterior depende del tipo de red (elección de [[DR]]/[[BDR]]).
![[Pasted image 20260219232754.png]]

### 4. Elección [[DR]] y [[BDR]]
En redes de acceso múltiple (Broadcast), el estado `Two-Way` es el momento crítico para la elección del [[DR]] (Router Designado) y el [[BDR]] (Backup DR).
![[Pasted image 20260219232853.png]]