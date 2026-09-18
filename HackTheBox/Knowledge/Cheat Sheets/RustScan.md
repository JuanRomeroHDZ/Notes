```
[Tú] Ejecutas: rustscan -a 10.10.10.5 -- -sC -sV
       │
       ▼
[Fase 1: Rustscan] Escanea 65,535 puertos en 3 segundos.
       │               Resultado: Puertos 22, 80 abiertos.
       ▼
[Fase 2: Relevo]   Rustscan construye el comando de Nmap por ti.
       │
       ▼
[Fase 3: Nmap]     Ejecuta automáticamente: nmap -p 22,80 -sC -sV 10.10.10.5
```
### 1. El concepto clave: La doble barra `--`
Todo lo que escribas **antes** de `--` son configuraciones de la velocidad y rangos de Rustscan.
Todo lo que escribas **después** de `--` son las "Nmap options" (los _flags_ de Nmap que ya estás aprendiendo en CPTS).

| **Comando**                   | **Para qué sirve**                                                                                                    |
| ----------------------------- | --------------------------------------------------------------------------------------------------------------------- |
| `rustscan -a <IP>`            | Escaneo básico. Encuentra puertos y corre un Nmap por defecto.                                                        |
| `rustscan -a <IP> -- -sC -sV` | **El más usado en HTB.** Encuentra puertos rápido y le dice a Nmap que lance scripts `-sC` y detecte versiones `-sV`. |
| `rustscan -a <IP> -- -A -Pn`  | Escaneo agresivo (`-A`) asumiendo que el host está vivo (`-Pn`).                                                      |
### 2. Controlando los Puertos (Fase Rustscan)

| **Comando / Flag**         | **Ejemplo**                  | **Descripción**                                   |
| -------------------------- | ---------------------------- | ------------------------------------------------- |
| `-p` (Puertos específicos) | `rustscan -a <IP> -p 22,80`  | Escanea solo esos puertos.                        |
| `-r` (Rango de puertos)    | `rustscan -a <IP> -r 1-1000` | Escanea del puerto 1 al 1000.                     |
| **Por defecto**            | `rustscan -a <IP>`           | Si no pones nada, escanea los **65,535** puertos. |
### 3. Velocidad Extrema (Afinando el motor)
A veces, en máquinas de HTB o entornos de laboratorio, Rustscan puede ir _demasiado_ rápido y perder puertos, o el sistema operativo le pone un límite de conexiones.

| **Comando / Flag** | **Ejemplo**                | **Descripción**                                                                                                        |
| ------------------ | -------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| `-b` (Batch size)  | `rustscan -a <IP> -b 500`  | Tamaño del lote de paquetes. Redúcelo (ej. 500) si la red es inestable y estás perdiendo puertos. Por defecto es 4500. |
| `-u` (Ulimit)      | `rustscan -a <IP> -u 5000` | Aumenta el límite de archivos abiertos en tu Linux. Ideal ponerlo en `5000` o más para evitar errores.                 |
| `-t` (Timeout)     | `rustscan -a <IP> -t 2000` | Tiempo de espera por puerto en milisegundos. Súbelo a 2000 o 3000 si hay lag.                                          |
## Ejemplos Prácticos para el CPTS

**Ejemplo 1: El inicio perfecto para una máquina de Hack The Box**
```
rustscan -a 10.10.11.200 -u 5000 -- -sC -sV -oN nmap_inicial.txt
```
- **Qué hace:** Escanea todos los puertos rapidísimo, le pasa los abiertos a Nmap, corre scripts básicos (`-sC`), detecta versiones (`-sV`) y te guarda el output en un archivo llamado `nmap_inicial.txt` (`-oN`).
**Ejemplo 2: Modo Sigiloso (Bajarle dos rayitas al ruido)**
```
rustscan -a 10.10.11.200 -b 500 -t 2000 -- -sS
```
- **Qué hace:** Envía paquetes en lotes pequeños de 500 (`-b 500`), espera 2 segundos por respuesta (`-t 2000`) y ejecuta el escaneo SYN de Nmap (`-sS`) que acabas de ver en tu temario de CPTS.

> **💡 El Consejo de Oro para CPTS:**
> En los exámenes o laboratorios, **Rustscan a veces omite puertos UDP**. Rustscan está optimizado para TCP. Cuando necesites escanear UDP (como el puerto 161 de SNMP o el 53 de DNS), es mejor que vuelvas al viejo y confiable Nmap puro: `sudo nmap -sU -p- <IP>`.