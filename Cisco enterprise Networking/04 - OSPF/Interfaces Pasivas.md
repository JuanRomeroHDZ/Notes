---
tipo: [[OSPF]]
tema: Interfaces Pasivas
estado: Completado
region: [[Parietal]]
---
# [[Passive Interface]]
De manera predeterminada, [[OSPF]] intenta enviar [[Hello Packets|mensajes Hello]] por todas las interfaces habilitadas. Esto genera tráfico innecesario y representa un riesgo de seguridad en segmentos donde no hay otros [[Router|routers]].

## Funcionamiento
La configuración de una [[Passive Interface|interfaz pasiva]] (`passive-interface`) cumple una función dual crucial:
1.  **Evita la transmisión:** Impide que el router envíe paquetes de enrutamiento ([[Hello Packets]]) a través de la interfaz.
2.  **Mantiene el anuncio:** La red conectada a esa interfaz sigue siendo anunciada a los demás vecinos [[OSPF]] conocidos.

![[Pasted image 20260302230641.png]]

## Configuración
Se utiliza frecuentemente en interfaces de usuario ([[LAN]]) o en [[Loopback Interface|interfaces de loopback]].

| Comando                                               | Descripción                                                                                                          |
| :---------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------- |
| `Router(config-router)# passive-interface [interfaz]` | Habilita la interfaz en modo pasivo.                                                                                 |
| `Router(config-router)# passive-interface default`    | Configura todas las interfaces como pasivas (requiere usar `no passive-interface` en las que sí deben enviar Hello). |

## Verificación
Para confirmar qué interfaces están operando como pasivas, se utiliza el comando `show ip protocols`.

![[Pasted image 20260302231020.png]]

> Nota: En una red con alta seguridad, se recomienda establecer `passive-interface default` y activar manualmente solo las interfaces donde realmente existen otros routers OSPF.