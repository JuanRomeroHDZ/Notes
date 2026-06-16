
El estado de enlace es un tipo de protocolo de enrutamiento en redes informáticas donde cada router informa a los demás sobre sus conexiones locales directas, vecinos y el coste de la ruta. Esta información permite a todos los routers crear un mapa detallado de la topología de la red para calcular la ruta más rápida. 

**Características clave del estado de enlace:**

- **Información compartida:** Cada router conoce los routers vecinos, el tipo de red (Ethernet, serial) y el coste del enlace.
- **Mapa topológico:** A diferencia de otros métodos, cada router mantiene una visión completa de la topología de la red (base de datos de estado de enlace).
- **Convergencia rápida:** Los routers detectan cambios (fallos o nuevas conexiones) y actualizan su mapa casi instantáneamente.
- **Protocolos comunes:** Los ejemplos principales son [[ospf]] (Open Shortest Path First) e IS-IS (Intermediate System to Intermediate System).
- **Eficiencia:** Se considera superior para redes grandes y complejas, ya que evita bucles y encuentra la ruta más corta (algoritmo SPF).
