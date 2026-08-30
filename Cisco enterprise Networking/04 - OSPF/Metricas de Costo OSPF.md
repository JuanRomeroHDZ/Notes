---
tipo: [[OSPF]]
tema: Métricas de Costo OSPF
estado: Completado
region: [[Parietal]]
---
# [[OSPF Cost Metrics]]
El protocolo [[OSPF]] utiliza una métrica (costo) para determinar la mejor ruta. Este costo es inversamente proporcional al [[Bandwidth|ancho de banda]] de la interfaz: a mayor ancho de banda, menor es el costo.

## Cálculo de Costo
La fórmula predeterminada utiliza un ancho de banda de referencia de 10^8 (100,000,000 bps):

`Costo = Referencia / Ancho de Banda`

![[Pasted image 20260310212132.png]]
![[Pasted image 20260310212242.png]]

> Nota: Si el resultado del cálculo es decimal, se redondea siempre al número entero más cercano (ej. 0.01 se redondea a 1).

## Ajuste de Referencia
Cambiar el costo de referencia no afecta la velocidad real de la interfaz, solo ajusta la métrica para ofrecer un cálculo más preciso en redes de alta velocidad (Gigabit/10Gigabit).

`Router(config-router)# auto-cost reference-bandwidth [Mbps]`

| Ejemplo | Comando |
| :--- | :--- |
| Configuración para 10 Gbps | `Router(config-router)# auto-cost reference-bandwidth 10000` |

> Importante: Este valor debe ser uniforme en todos los routers de la red [[OSPF]] para garantizar la consistencia en el cálculo de rutas.

![[Pasted image 20260310214043.png]]

## [[Accumulated Cost]]
El costo total es la suma de los costos de cada interfaz en el camino, incluyendo el costo de la [[Loopback Interface|interfaz loopback]] (predeterminado en 1).

![[Pasted image 20260310215255.png]]
![[Pasted image 20260310215809.png]]

## Métodos de Manipulación de Costo

| Método | Recomendación | Nota |
| :--- | :--- | :--- |
| `ip ospf cost [valor]` | **Recomendado** | Método directo y preciso para manipular el costo de una interfaz específica. |
| `bandwidth [kbps]` | No recomendado | Modifica la métrica pero puede afectar a otros procesos. Solo funciona consistentemente en equipos [[Cisco]]. |

![[Pasted image 20260310215907.png]]