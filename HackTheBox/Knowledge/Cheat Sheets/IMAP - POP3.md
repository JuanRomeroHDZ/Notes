# Cheat sheet de IMAP y POP3

## 1. Puertos clave

|Puerto|Protocolo|Cifrado|
|---|---|---|
|110|POP3|Ninguno (o STLS con STARTTLS)|
|995|POP3S|TLS desde el inicio|
|143|IMAP|Ninguno (o STARTTLS)|
|993|IMAPS|TLS desde el inicio|
## 2. Diferencia rápida

| Aspecto           | POP3                                        | IMAP                                           |
| ----------------- | ------------------------------------------- | ---------------------------------------------- |
| Modelo            | Descarga y (normalmente) borra del servidor | Sincroniza y mantiene el correo en el servidor |
| Carpetas          | Solo buzón de entrada                       | Carpetas, subcarpetas y etiquetas              |
| Multi-dispositivo | Malo                                        | Excelente                                      |
| Uso típico        | Un solo equipo, acceso offline              | Varios dispositivos, webmail                   |
## 3. Comandos POP3

| Comando | Función                           | Ejemplo        |
| ------- | --------------------------------- | -------------- |
| `USER`  | Usuario                           | `USER juan`    |
| `PASS`  | Contraseña                        | `PASS secreto` |
| `STAT`  | Número de mensajes y tamaño total | `STAT`         |
| `LIST`  | Lista mensajes y tamaños          | `LIST`         |
| `RETR`  | Descarga un mensaje               | `RETR 1`       |
| `DELE`  | Marca un mensaje para borrar      | `DELE 1`       |
| `TOP`   | Cabeceras y N líneas del cuerpo   | `TOP 1 10`     |
| `UIDL`  | ID único de cada mensaje          | `UIDL`         |
| `RSET`  | Quita las marcas de borrado       | `RSET`         |
| `NOOP`  | Mantiene viva la sesión           | `NOOP`         |
| `CAPA`  | Lista capacidades del servidor    | `CAPA`         |
| `STLS`  | Cambia a TLS                      | `STLS`         |
| `QUIT`  | Cierra y aplica borrados          | `QUIT`         |

## 4. Comandos IMAP

| Comando             | Función                                | Ejemplo                             |
| ------------------- | -------------------------------------- | ----------------------------------- |
| `LOGIN`             | Autenticación                          | `a1 LOGIN juan secreto`             |
| `AUTHENTICATE`      | Autenticación con SASL (OAuth, PLAIN)  | `a1 AUTHENTICATE PLAIN`             |
| `CAPABILITY`        | Extensiones soportadas                 | `a1 CAPABILITY`                     |
| `LIST`              | Lista carpetas                         | `a2 LIST "" "*"`                    |
| `LSUB`              | Carpetas suscritas                     | `a2 LSUB "" "*"`                    |
| `SELECT`            | Abre una carpeta (lectura y escritura) | `a3 SELECT INBOX`                   |
| `EXAMINE`           | Abre una carpeta en solo lectura       | `a3 EXAMINE INBOX`                  |
| `STATUS`            | Contadores sin abrir la carpeta        | `a4 STATUS INBOX (MESSAGES UNSEEN)` |
| `FETCH`             | Lee mensajes o partes                  | `a5 FETCH 1 (FLAGS BODY[HEADER])`   |
| `SEARCH`            | Busca mensajes                         | `a6 SEARCH UNSEEN FROM "ana"`       |
| `STORE`             | Cambia flags (leído, borrado)          | `a7 STORE 1 +FLAGS (\Seen)`         |
| `COPY`              | Copia a otra carpeta                   | `a8 COPY 1 Archivo`                 |
| `MOVE`              | Mueve (extensión)                      | `a8 MOVE 1 Archivo`                 |
| `CREATE` / `DELETE` | Crea o borra carpetas                  | `a9 CREATE Proyectos`               |
| `EXPUNGE`           | Elimina definitivamente los marcados   | `a10 EXPUNGE`                       |
| `IDLE`              | Notificaciones en tiempo real          | `a11 IDLE`                          |
| `STARTTLS`          | Cambia a TLS                           | `a0 STARTTLS`                       |
| `LOGOUT`            | Cierra la sesión                       | `a12 LOGOUT`                        |

## 5. Flags IMAP

| Flag        | Significado                         |
| ----------- | ----------------------------------- |
| `\Seen`     | Leído                               |
| `\Answered` | Respondido                          |
| `\Flagged`  | Marcado como importante             |
| `\Deleted`  | Marcado para borrar (hasta EXPUNGE) |
| `\Draft`    | Borrador                            |
| `\Recent`   | Llegó desde la última sesión        |

## 6. Códigos de respuesta

| Código         | Significado                                |
| -------------- | ------------------------------------------ |
| `+OK` (POP3)   | Comando exitoso                            |
| `-ERR` (POP3)  | Error                                      |
| `OK` (IMAP)    | Comando exitoso                            |
| `NO` (IMAP)    | Fallo del comando                          |
| `BAD` (IMAP)   | Error de sintaxis o comando inválido       |
| `* BYE` (IMAP) | El servidor cierra la conexión             |
| `+` (IMAP)     | Continuación, el servidor espera más datos |

## 7. Flujo de sesión POP3

```
S: +OK POP3 server ready
C: USER juan
S: +OK
C: PASS secreto
S: +OK Logged in
C: STAT
S: +OK 2 4096
C: RETR 1
S: +OK 2048 octets
   (mensaje)
C: DELE 1
S: +OK marked for deletion
C: QUIT
S: +OK Bye
```

## 8. Flujo de sesión IMAP

```
S: * OK IMAP4rev1 ready
C: a1 LOGIN juan secreto
S: a1 OK LOGIN completed
C: a2 SELECT INBOX
S: * 12 EXISTS
S: * 2 RECENT
S: a2 OK [READ-WRITE] SELECT completed
C: a3 FETCH 12 (FLAGS BODY[HEADER.FIELDS (SUBJECT FROM)])
S: * 12 FETCH (FLAGS (\Seen) BODY[...] {...})
S: a3 OK FETCH completed
C: a4 LOGOUT
S: * BYE LOGOUT
S: a4 OK LOGOUT completed
```

## 9. Herramientas recomendadas

| Herramienta                                         | Para qué sirve                                  |
| --------------------------------------------------- | ----------------------------------------------- |
| `openssl s_client -connect host:993`                | Hablar IMAP cifrado a mano                      |
| `openssl s_client -connect host:995`                | Hablar POP3 cifrado a mano                      |
| `nc` / `telnet`                                     | Interacción en texto plano (puertos 110 y 143)  |
| `nmap -sV -p110,143,993,995 host`                   | Detectar servicios y versiones                  |
| `nmap --script pop3-capabilities,imap-capabilities` | Ver extensiones soportadas                      |
| `nmap --script pop3-ntlm-info,imap-ntlm-info`       | Extraer información de NTLM                     |
| `hydra -L users.txt -P pass.txt imap://host`        | Fuerza bruta (solo en laboratorios autorizados) |
| `evolution`, `thunderbird`                          | Clientes para probar configuraciones            |
| `Wireshark` (filtros `imap` y `pop`)                | Analizar sesiones en capturas                   |

## 10. Ejemplo práctico

```bash
# Leer la bandeja con curl (IMAP)
curl -u juan:secreto "imaps://imap.ejemplo.com/INBOX?ALL"

# Ver un mensaje concreto
curl -u juan:secreto "imaps://imap.ejemplo.com/INBOX;UID=5"

# Listar mensajes con POP3
curl -u juan:secreto "pop3s://pop.ejemplo.com/"
```

## 11. Ideas para practicar en HackTheBox

- Revisa `nmap -sV` en 110, 143, 993 y 995. Si ves credenciales por defecto o cuentas sin cifrar, anótalo.
- Prueba `CAPA` y `CAPABILITY` para ver qué autenticación acepta el servidor (PLAIN, NTLM, XOAUTH2).
- Si hay NTLM, `nmap --script pop3-ntlm-info` puede revelar el nombre del dominio y del host.