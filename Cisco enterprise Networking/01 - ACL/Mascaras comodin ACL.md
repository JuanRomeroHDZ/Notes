---
tipo: [[Wildcard Mask]]
tema: Mascaras comodin ACL
estado: Completado
region: [[Parietal]]
---
# [[Wildcard Mask]]
En las [[Access Control List|ACL]] se usan las [[Wildcard Mask]] para determinar qué bits ignorar o usar en cuanto una dirección de red o [[Host]].

## Coincidir con [[Host]]
En este caso, que solo es un host y quieres permitir o denegar, como solo es uno y quieres que coincida, usas la [[Wildcard Mask]] de cuádruple 0, o sea 0.0.0.0.
![[Pasted image 20260406135130.png]]
![[Pasted image 20260406135142.png]]

## Coincidir con [[Subnet|subred IPv4]]
En este caso la [[ACE]] necesita permitir todos los host de la red 192.168.1.0 /24; en este caso la [[Wildcard Mask]] sería 0.0.0.255.
![[Pasted image 20260406135331.png]]

## Coincidir con Rango de [[Host]]
En este caso se tiene una [[Access Control List|ACL]] que quiere permitir o trabajar en un rango de direcciones de 192.168.16.0/24 a 192.168.31.0/24; en este caso la [[Wildcard Mask]] sería 0.0.15.255 que abarca todo ese rango de direcciones. 
![[Pasted image 20260406141941.png]]

## Palabras clave
Las dos palabras clave son:
* [[Host keyword|host]]: Esta palabra clave sustituye a la máscara 0.0.0.0. Esta máscara indica que todos los bits de direcciones [[IPv4]] deben coincidir para filtrar solo una dirección de host.
* [[Any keyword|any]]: Esta palabra clave sustituye a la máscara 255.255.255.255. Esta máscara establece que se omita la dirección [[IPv4]] completa o que se acepte cualquier dirección.
![[Pasted image 20260406142226.png]]