---
tipo: [[OSPF]]
tema: Máscara Wildcard
estado: Completado
region: [[Parietal]]
---
# [[Wildcard Mask]]
La [[Wildcard Mask|máscara wildcard]] en la mayoría de las situaciones es la inversa de la [[Subnet Mask|máscara de subred]] configurada. 

## Cálculo de la Wildcard
En general, la wildcard se puede obtener restando la máscara de subred a la dirección completa `255.255.255.255`, lo que equivale a invertir los números binarios (aplicar un NOT lógico a los bits de la máscara).

Por ejemplo, si la máscara de una dirección [[IPv4]] es `/24`:

| Formato | Máscara de Subred (/24) | Máscara Wildcard Inversa |
| :--- | :--- | :--- |
| **Decimal** | 255.255.255.0 | 0.0.0.255 |
| **Binario** | 11111111.11111111.11111111.00000000 | 00000000.00000000.00000000.11111111 |

![[Pasted image 20260302223441.png]]
![[Pasted image 20260302223501.png]]