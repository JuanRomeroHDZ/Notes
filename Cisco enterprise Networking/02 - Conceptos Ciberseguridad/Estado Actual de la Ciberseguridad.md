---
tipo: [[Ciberseguridad]]
tema: Estado Actual de la Ciberseguridad
estado: Completado
region: [[Parietal]]
---
# [[Estado Actual de la Ciberseguridad]]
## [[Conceptos Fundamentales]]
* [[Asset|Activo]]: Cualquier cosa con valor para la organización (personas, equipos, recursos, datos, etc.).
* [[Vulnerability|Vulnerabilidad]]: Debilidad en un sistema o su diseño que podrá ser explotada por una amenaza.
* [[Threat|Amenaza]]: Potencial peligro para los activos o datos de una red con funcionalidad de enrutamiento.
* [[Exploit|Explotar]]: Mecanismo para tomar ventaja de una vulnerabilidad.
* [[Mitigation|Mitigación]]: Contramedida que reduce la probabilidad o gravedad de una posible amenaza o riesgo.
* [[Risk|Riesgo]]: Probabilidad de que una amenaza explote la vulnerabilidad de un activo afectando negativamente a la organización. Se mide por la probabilidad de ocurrencia y sus consecuencias.

## [[Attack Vectors]]
Un [[Attack Vector|vector de ataque]] es una ruta por la cual una amenaza puede obtener acceso al servidor, host o red. Se originan dentro o fuera de la red corporativa.
* [[DoS|Ataque DoS]]: Un dispositivo o aplicación de red está incapacitado y no puede admitir solicitudes de usuarios legítimos.

### Amenazas Internas
Un usuario interno (empleado o consultor) puede, accidental o intencionalmente:
* Robar y copiar datos confidenciales (correos, dispositivos de almacenaje, etc.).
* Comprometer servidores internos o infraestructura.
* Desconectar conexiones críticas.
* Conectar unidades [[USB]] infectadas.
Las amenazas internas suelen causar mayores daños que las externas debido al acceso directo y conocimiento de la red.

## [[Data Loss]]
Los datos son el activo más valioso. 
### [[Data Loss Vectors]]
* [[Email]] / [[Redes Sociales]]: Mensajes interceptados o capturados.
* [[Dispositivos no encriptados]]: Recuperación de datos sin algoritmos de cifrado.
* [[Cloud Storage]]: Compromiso por configuraciones de seguridad débiles.
* [[Removable Media]]: Extracción de datos mediante [[USB]] ajenos.
* [[Physical Backup]]: Falta de trituración de datos físicos.
* [[Access Control]] Incorrecto: Contraseñas débiles.

## [[Hacking Tools]]
![[Pasted image 20260322173338.png]]

| Categoría | Descripción | Herramientas |
| :--- | :--- | :--- |
| [[Password Recovery]] | Descifrado o recuperación de claves | John the Ripper, Ophcrack, L0phtCrack, THC Hydra, RainbowCrack, Medusa |
| [[Wireless Hacking]] | Detección de vulnerabilidades en redes WiFi | Aircrack-ng, Kismet, InSSIDer, KisMAC, Firesheep, NetStumbler |
| [[Network Scanning]] | Sondeo de puertos [[TCP]] / [[UDP]] | Nmap, SuperScan, Angry IP Scanner, NetScanTools |
| [[Packet Crafting]] | Prueba de [[Firewall]] con paquetes forjados | Hping, Scapy, Socat, Yersinia, Netcat, Nping, Nemesis |
| [[Protocol Analysis]] | Análisis de tráfico [[LAN]] / [[WLAN]] | Wireshark, Tcpdump, Ettercap, Dsniff, EtherApe, Paros, Fiddler, Ratproxy, SSLstrip |
| [[Rootkit Detection]] | Integridad de directorios y archivos | AIDE, Netfilter, PF: OpenBSD Packet Filter |
| [[Fuzzing]] | Descubrimiento de vulnerabilidades | Skipfish, Wapiti, W3af |
| [[Digital Forensics]] | Detección de rastros y evidencia | Sleuth Kit, Helix, Maltego, Encase |
| [[Debugging]] | Ingeniería inversa / Análisis de malware | GDB, WinDbg, IDA Pro, Immunity Debugger |
| [[Hacking OS]] | Sistemas precargados con herramientas | Kali Linux, Knoppix, BackBox Linux |
| [[Encryption Tools]] | Codificación de datos | VeraCrypt, CipherShed, OpenSSH, OpenSSL, Tor, OpenVPN, Stunnel |
| [[Vulnerability Exploitation]] | Identificación de vulnerabilidad en host remoto | Metasploit, Core Impact, Sqlmap, Social Engineer Toolkit, Netsparker |
| [[Vulnerability Assessment]] | Escaneo de puertos y vulnerabilidades | Nipper, Secunia Nipper, Secuna PSI, Core Impact, Nessus v6, SAINT, Open VAS |
| [[Wireless Analysis]] | Análisis de redes | Vistumbler |