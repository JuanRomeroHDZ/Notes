---
tipo: [[OSPF]]
tema: OSPF Multiárea
estado: Completado
region: [[Parietal]]
---
# [[Multi-Area OSPF]]

[[Multi-Area OSPF]] es la solución jerárquica para redes grandes donde una sola área compromete la estabilidad debido a la carga del procesador y el tamaño de la [[Link State Database|LSDB]].

## Problemas de una red OSPF masiva
Si el área es demasiado grande, el algoritmo [[SPF Algorithm|SPF]] (Dijkstra) y el mantenimiento de la [[LSDB]] se vuelven ineficientes:
*   **Carga de CPU:** El cálculo de rutas exige un alto costo de procesamiento.
*   **Inestabilidad:** Cualquier cambio en la topología obliga a todos los routers a re-ejecutar el [[SPF Algorithm|SPF]].
*   **Rendimiento:** Routers con recursos limitados pueden quedar fuera de la tabla de enrutamiento al no poder procesar la información.

## Solución: Arquitectura Jerárquica

| Característica            | Impacto de Multi-Area                                                                                     |
| :------------------------ | :-------------------------------------------------------------------------------------------------------- |
| **Aislamiento de fallos** | Los cambios en un área no obligan a re-calcular [[SPF]] en las áreas vecinas.                             |
| **Eficiencia de LSDB**    | Los [[Area Border Router \| ABR]] resumen la información, reduciendo el tamaño de la base de datos local. |
| **Tráfico de control**    | Los [[LSA]] se limitan a su propia área, reduciendo el tráfico innecesario.                               |

Los [[Area Border Router|ABR]] son los routers fronterizos encargados de mantener la [[LSDB]] de cada área y comunicarse con el área líder (el [[Backbone Area|Área 0]]). Si un área falla, las demás no se ven perjudicadas porque no necesitan re-ejecutar el algoritmo, simplemente se comunican con el [[ABR]] afectado.

![[Pasted image 20260207222854.png]]