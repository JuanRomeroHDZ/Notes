

en las acl se se usan las wildcard mask para determinar que bits ignorar o usar en cuanto una dirección de red o host.

ejemplos

- comodín para coincidir con host.

en este caso que solo es un host y quieres permitir o denegar como sol es uno y quieres que coincida usas la wildcard de cuádruple 0 osea 0.0.0.0

![[Pasted image 20260406135130.png]]

![[Pasted image 20260406135142.png]]

- comodín para que coincida con subred ipv4


en este caso la ACE necesita perimitir todos los host de la red 192.168.1.0 /24 en este caso la wildcard seria 0.0.0.255

![[Pasted image 20260406135331.png]]


- Comodin que coincida con un rango de host

en este caso se tiene una ACL qu quiere permitir o trabajar en un rango de direcciones de 192.168.16.0/24  a  192.168.31.0/24 en este caso la wildcard seria 0.0.15.255 que abarca todo ese rango de direcciones. 

![[Pasted image 20260406141941.png]]



Las dos palabras clave son:

. host - esta palabra clave sustituye a la máscara 0.0.0.0. Esta máscara indica que todos los bits de direcciones IPv4 deben coincidir para
filtrar solo una dirección de host.
· any - esta palabra clave sustituye a la máscara 255.255.255.255. Esta máscara establece que se omita la dirección IPv4 completa o que
se acepte cualquier dirección.
![[Pasted image 20260406142226.png]]