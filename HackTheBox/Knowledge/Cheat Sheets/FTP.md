| **Comando**      | **Descripción**                                                                                                        |
| ---------------- | ---------------------------------------------------------------------------------------------------------------------- |
| **`!`**          | Ejecuta el comando especificado en la computadora local.                                                               |
| **`?`**          | Muestra descripciones para los comandos FTP (igual que `help`).                                                        |
| **`append`**     | Adjunta un archivo local a un archivo en la computadora remota.                                                        |
| **`ascii`**      | Configura el tipo de transferencia de archivos en modo ASCII (por defecto).                                            |
| **`bell`**       | Activa/desactiva un sonido de campana tras completar cada comando de transferencia de archivos (por defecto = OFF).    |
| **`binary`**     | Configura el tipo de transferencia de archivos en modo binario.                                                        |
| **`bye`**        | Finaliza la sesión de FTP y sale de la aplicación (igual que `quit`).                                                  |
| **`cd`**         | Cambia el directorio de trabajo en la computadora remota.                                                              |
| **`close`**      | Finaliza la sesión de FTP y regresa al intérprete de comandos.                                                         |
| **`debug`**      | Activa/desactiva el modo de depuración (por defecto = OFF).                                                            |
| **`delete`**     | Elimina un solo archivo en una computadora remota.                                                                     |
| **`dir`**        | Muestra una lista de los archivos y subdirectorios de un directorio remoto.                                            |
| **`disconnect`** | Se desconecta de la computadora remota, reteniendo el símbolo del sistema (`ftp>`).                                    |
| **`get`**        | Copia un único archivo remoto a la computadora local.                                                                  |
| **`glob`**       | Activa/desactiva el uso de comodines (_filename globbing_) (por defecto = ON).                                         |
| **`hash`**       | Activa/desactiva la impresión del signo de almohadilla (`#`) por cada bloque de datos transferido (por defecto = OFF). |
| **`help`**       | Muestra descripciones para los comandos FTP (igual que `?`).                                                           |
| **`lcd`**        | Cambia el directorio de trabajo en la computadora local.                                                               |
| **`literal`**    | Envía argumentos de forma literal al servidor FTP remoto (igual que `quote`).                                          |
| **`ls`**         | Muestra una lista abreviada de los archivos y subdirectorios de un directorio remoto.                                  |
| **`mdelete`**    | Elimina uno o más archivos en una computadora remota.                                                                  |
| **`mdir`**       | Muestra una lista de un directorio remoto (permite múltiples archivos).                                                |
| **`mget`**       | Copia uno o más archivos remotos a la computadora local.                                                               |
| **`mkdir`**      | Crea un directorio remoto.                                                                                             |
| **`mls`**        | Muestra una lista abreviada de un directorio remoto (permite múltiples archivos).                                      |
| **`mput`**       | Copia uno o más archivos locales a la computadora remota.                                                              |
| **`open`**       | Se conecta al servidor FTP especificado.                                                                               |
| **`prompt`**     | Activa/desactiva las preguntas interactivas durante transferencias múltiples (por defecto = ON).                       |
| **`put`**        | Copia un único archivo local a la computadora remota (igual que `send`).                                               |
| **`pwd`**        | Muestra el directorio actual en la computadora remota (_print working directory_).                                     |
| **`quit`**       | Finaliza la sesión FTP y sale de la aplicación (igual que `bye`).                                                      |
| **`quote`**      | Envía argumentos de forma literal al servidor FTP remoto (igual que `literal`).                                        |
| **`recv`**       | Copia un archivo remoto a la computadora local (igual que `get`).                                                      |
| **`remotehelp`** | Muestra ayuda para los comandos remotos.                                                                               |
| **`rename`**     | Renombra archivos en la computadora remota.                                                                            |
| **`rmdir`**      | Elimina un directorio remoto.                                                                                          |
| **`send`**       | Copia un archivo local a la computadora remota (igual que `put`).                                                      |
| **`status`**     | Muestra el estado actual de las conexiones FTP.                                                                        |
| **`trace`**      | Activa/desactiva el rastreo de paquetes (por defecto = OFF).                                                           |
| **`type`**       | Configura o muestra el tipo de transferencia de archivos (por defecto = ASCII).                                        |
| **`user`**       | Especifica un usuario para iniciar sesión en la computadora remota.                                                    |
| **`verbose`**    | Activa/desactiva el modo detallado (por defecto = ON).                                                                 |

## ⚡ Opciones de Línea de Comandos (`Command Line`)

Estas opciones se utilizan al iniciar el comando `ftp` desde la terminal de tu sistema operativo:

|**Opción**|**Descripción**|
|---|---|
|**`-v`**|Suprime la visualización detallada (_verbose_) de las respuestas del servidor remoto.|
|**`-n`**|Suprime el inicio de sesión automático (_auto login_).|
|**`-i`**|Desactiva las preguntas interactivas durante las transferencias de múltiples archivos.|
|**`-d`**|Habilita la depuración, mostrando todos los comandos FTP pasados entre el cliente y el servidor.|
|**`–g`**|Desactiva el uso de comodines (_filename globbing_), los cuales permiten usar caracteres comodín en nombres de rutas y archivos locales.|
|**`-s:filename`**|Especifica un archivo de texto que contiene comandos FTP; estos se ejecutarán automáticamente al iniciar `ftp`. No se permiten espacios en este parámetro (se usa en lugar de la redirección `>`).|
|**`-a`**|Utiliza cualquier interfaz local al enlazar la conexión de datos.|
|**`-w:windowsize`**|Sobrescribe el tamaño predeterminado del búfer de transferencia (que por defecto es 4096).|
|**`computer`**|Especifica el nombre de la computadora o la dirección IP remota a la cual conectarse (este parámetro, de incluirse, **debe ser el último** en la línea de comandos).|
