---
tipo: [[OSPF]]
tema: Paquetes OSPF
estado: Completado
region: [[Parietal]]
---
# [[OSPF Packets]]

Los paquetes de estado de enlace son las herramientas principalmente utilizadas por [[OSPF]] para determinar la ruta más rápida disponible, establecer y mantener adyacencias, e intercambiar actualizaciones de enrutamiento.

## Tipos de paquetes

| Tipo | Nombre                                 | Función                                                                     |
| :--- | :------------------------------------- | --------------------------------------------------------------------------- |
| 1    | [[Hello Packet]]                       | Descubre vecinos y construye adyacencias.                                   |
| 2    | [[Database Description \| DBD]]        | Controla la sincronización de las bases de datos entre los routers.         |
| 3    | [[Link-State Request \| LSR]]          | Solicita registros específicos de estado de enlace de router a router.      |
| 4    | [[Link-State Update \| LSU]]           | Envía los registros de estado de enlace solicitados (respuesta al [[LSR]]). |
| 5    | [[Link-State Acknowledgment \| LSAck]] | Reconoce los demás tipos de paquetes; confirma la recepción de un [[LSU]].  |

![[Pasted image 20260208165017.png]]

## Intercambio y Actualizaciones
El estado de enlace es un algoritmo que permite a cada router construir un mapa detallado de la topología completa.

1.  **Intercambio inicial:** Los routers intercambian paquetes [[DBD]] (tipo 2), que son una lista abreviada de la [[Link State Database|LSDB]] del router emisor. Se emplean para verificar con la [[LSDB]] local.
2.  **Solicitud:** Los routers receptores usan paquetes [[LSR]] (tipo 3) para solicitar más información sobre una entrada de la [[DBD]].
3.  **Respuesta:** El paquete [[LSU]] (tipo 4) se usa para responder al [[LSR]], proporcionando la información requerida.

> Nota: Los paquetes [[LSU]] también se usan para reenviar actualizaciones de la red (cambios de estado de enlace). Un paquete [[LSU]] puede contener uno o más [[LSA|LSA (Link State Advertisements)]]. Es importante no confundir [[LSU]] con [[LSA]].

![[Pasted image 20260208170845.png]]

## [[Hello Packet]] (Tipo 1)
El paquete [[OSPF]] tipo 1 es el paquete [[Hello]]. El paquete [[Hello]] se usa para descubrir vecinos y construir las adyacencias entre ellos.