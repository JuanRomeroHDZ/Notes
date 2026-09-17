Un **cheat sheet** estructurado y de referencia rápida para **cURL**, organizado por casos de uso operativos: desde peticiones básicas e inspección de APIs hasta depuración de red, manejo de SSL y medición de latencia.
## 1. Opciones Generales y Modos de Salida

| **Flag**    | **Nombre / Equivalente largo** | **Descripción**                                                          |
| ----------- | ------------------------------ | ------------------------------------------------------------------------ |
| `-s`        | `--silent`                     | Modo silencioso; oculta barra de progreso y mensajes de error.           |
| `-S`        | `--show-error`                 | Usado junto con `-s`, muestra errores si la petición falla.              |
| `-v`        | `--verbose`                    | Muestra el handshake, cabeceras enviadas (`>`) y recibidas (`<`).        |
| `-i`        | `--include`                    | Incluye los encabezados de respuesta HTTP en la salida estándar.         |
| `-I`        | `--head`                       | Envía una petición `HEAD` para recuperar únicamente las cabeceras.       |
| `-L`        | `--location`                   | Sigue redirecciones HTTP (`301`, `302`, `307`, `308`).                   |
| `-k`        | `--insecure`                   | Permite conexiones SSL/TLS inseguras (ignora certificados autofirmados). |
| `-4` / `-6` | `--ipv4` / `--ipv6`            | Fuerza la resolución y conexión mediante IPv4 o IPv6.                    |
## 2. Métodos HTTP y Envío de Datos

### Métodos Básicos
```
# GET (por defecto)
curl https://api.ejemplo.com/recursos

# HEAD (solo cabeceras)
curl -I https://api.ejemplo.com/recursos

# DELETE
curl -X DELETE https://api.ejemplo.com/recursos/42

# PUT (con datos)
curl -X PUT https://api.ejemplo.com/recursos/42 -d "activo=true"
```
### Envío de Formularios y JSON
```
# Envío nativo de JSON (agrega automáticamente Content-Type: application/json)
curl --json '{"usuario": "alex", "rol": "admin"}' https://api.ejemplo.com/usuarios

# Envío clásico de JSON manual
curl -X POST https://api.ejemplo.com/usuarios \
  -H "Content-Type: application/json" \
  -d '{"usuario": "alex", "rol": "admin"}'

# Cargar JSON desde archivo
curl -X POST https://api.ejemplo.com/usuarios \
  -H "Content-Type: application/json" \
  -d @datos.json

# Formulario estándar URL-encoded (application/x-www-form-urlencoded)
curl -X POST https://ejemplo.com/login \
  -d "user=admin" \
  -d "pass=secreto123"

# Subida Multipart / Form-Data (-F para archivos o campos mixtos)
curl -X POST https://api.ejemplo.com/upload \
  -F "archivo=@/ruta/imagen.png" \
  -F "descripcion=Logo oficial"
```
## 3. Cabeceras, Cookies y Autenticación
### Encabezados Personalizados
```
# Definir cabeceras HTTP (-H)
curl -H "Accept: application/json" \
  -H "X-Custom-Header: Valor" \
  https://api.ejemplo.com/items

# Modificar o vaciar cabeceras predeterminadas (ponerla sin valor la elimina)
curl -H "User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64)" \
  -H "Accept:" \
  https://ejemplo.com
```
### Autenticación
```
# HTTP Basic Authentication (-u usuario:password)
curl -u admin:secreto123 https://api.ejemplo.com/admin

# Bearer Token (OAuth2 / JWT)
curl -H "Authorization: Bearer <TOKEN_AQUI>" https://api.ejemplo.com/perfil

# Clave de API personalizada
curl -H "X-API-Key: abc123xyz" https://api.ejemplo.com/metricas
```
### Manejo de Sesiones y Cookies
```
# Guardar cookies de respuesta en un archivo (-c)
curl -c cookies.txt https://ejemplo.com/login -d "user=admin&pass=123"

# Enviar cookies almacenadas en peticiones posteriores (-b)
curl -b cookies.txt https://ejemplo.com/panel

# Enviar una cookie directa inline
curl -b "session_id=987654321; tracking=false" https://ejemplo.com/datos
```
## 4. Descarga y Subida de Archivos

|**Operación**|**Comando**|
|---|---|
|**Guardar con nombre personalizado**|`curl -o archivo_local.zip [https://ejemplo.com/remoto.zip](https://ejemplo.com/remoto.zip)`|
|**Guardar con nombre original del servidor**|`curl -O [https://ejemplo.com/instalador.tar.gz](https://ejemplo.com/instalador.tar.gz)`|
|**Definir directorio de descarga**|`curl --output-dir /tmp/descargas -O [https://ejemplo.com/doc.pdf](https://ejemplo.com/doc.pdf)`|
|**Reanudar descarga interrumpida**|`curl -C - -O [https://ejemplo.com/archivo_pesado.iso](https://ejemplo.com/archivo_pesado.iso)`|
|**Descarga con límite de velocidad**|`curl --limit-rate 500k -O [https://ejemplo.com/backup.dump](https://ejemplo.com/backup.dump)`|
|**Subir vía FTP / SFTP**|`curl -T archivo.txt -u usuario:pass ftp://[ftp.ejemplo.com/ruta/](https://ftp.ejemplo.com/ruta/)`|
## 5. Proxies, Redes y Evasión DNS
```
# Pasar tráfico por un proxy HTTP/HTTPS
curl -x http://proxy.empresa.local:8080 https://api.ejemplo.com

# Pasar tráfico por un proxy SOCKS5 (ej. Tor)
curl --socks5-hostname 127.0.0.1:9050 https://check.torproject.org

# Forzar resolución DNS personalizada sin editar /etc/hosts (--resolve HOST:PUERTO:IP)
curl --resolve mi-dominio.com:443:192.168.1.150 https://mi-dominio.com

# Forzar versión HTTP
curl --http1.1 https://ejemplo.com
curl --http2 https://ejemplo.com
curl --http3 https://ejemplo.com
```
## 6. Timeouts y Control de Tiempos

|**Flag**|**Función**|**Ejemplo**|
|---|---|---|
|`--connect-timeout <seg>`|Tiempo máximo esperando establecer el handshake TCP.|`curl --connect-timeout 5 [https://ejemplo.com](https://ejemplo.com)`|
|`-m`, `--max-time <seg>`|Tiempo límite máximo para la operación completa.|`curl -m 15 [https://ejemplo.com/endpoint-lento](https://ejemplo.com/endpoint-lento)`|
|`--retry <n>`|Reintenta la petición _n_ veces ante fallos temporales (5xx/timeouts).|`curl --retry 3 --retry-delay 2 [https://api.ejemplo.com](https://api.ejemplo.com)`|
## 7. Depuración Avanzada y Análisis de Latencia

### Volcado Completo de Tráfico (Raw Dump)
```
# Inspeccionar paquetes ASCII enviados y recibidos (ideal para depurar SSL o cabeceras)
curl --trace-ascii trace_debug.log https://api.ejemplo.com
```
### Medición de Tiempos y Rendimiento (`--write-out` / `-w`)
Permite extraer métricas milimétricas del ciclo de vida de la conexión:
```
curl -s -o /dev/null -w "\
Código HTTP:       %{http_code}\n\
Resolución DNS:    %{time_namelookup} s\n\
Conexión TCP:      %{time_connect} s\n\
Negociación TLS:   %{time_appconnect} s\n\
Primer Byte (TTFB):%{time_starttransfer} s\n\
Tiempo Total:      %{time_total} s\n" \
https://ejemplo.com
```
