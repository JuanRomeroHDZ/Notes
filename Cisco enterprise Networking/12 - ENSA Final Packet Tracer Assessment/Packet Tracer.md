## Topology
![[Pasted image 20260626084942.png]]

# 🖥️ ENSA Final - Packet Tracer Assessment

> [!IMPORTANT]
> 
> **Reglas del Examen:**
> 
> - No uses el botón **Atrás** del navegador ni recargues la ventana del examen.
>     
> - No cierres Packet Tracer manualmente al terminar; se cerrará automáticamente.
>     
> - Haz clic en el botón **Submit Assessment** para enviar tu trabajo.
>     

> [!NOTE]
> 
> **Escenario:**
> 
> En esta evaluación de Packet Tracer, configurarás los dispositivos de una pequeña red. Completarás todas las tareas en el **Modo Físico de PT**. No tendrás acceso a la topología lógica.
> 
> Colocarás los dispositivos en las ubicaciones adecuadas y los encenderás. Configurarás routers, switches y PCs para admitir conectividad IPv4 para los hosts. Los routers y switches deben gestionarse de forma segura. Configurarás OSPFv2 de una sola área, NAT y listas de control de acceso. Además, realizarás una copia de seguridad de tus configuraciones operativas en un servidor TFTP y cargarás una configuración operativa en otro dispositivo. Por otra parte, se utilizan diferentes versiones de la imagen de IOS en los switches. Actualizarás un switch para usar el último IOS.

## 📋 Tabla de Direccionamiento

| **Nombre del Dispositivo**             | **Interfaz** | **Dirección IP**   | **Gateway por Defecto** |
| -------------------------------------- | ------------ | ------------------ | ----------------------- |
| **R1**                                 | G0/0/0       | 198.51.100.1/30    | N/A                     |
| _ERROR: VARIABLE NOT FOUND [[R1Name]]_ | G0/0/1       | 192.168.1.1/24     | N/A                     |
| _ERROR: VARIABLE NOT FOUND [[R1Name]]_ | G0/0/2       | 64.100.1.1/29      | N/A                     |
| **R2**                                 | G0/0/0       | 198.51.100.2/30    | N/A                     |
| _ERROR: VARIABLE NOT FOUND [[R2Name]]_ | G0/0/1       | 172.16.2.1/24      | N/A                     |
| _ERROR: VARIABLE NOT FOUND [[R2Name]]_ | G0/0/2       | 209.165.202.129/27 | N/A                     |
| **S1**                                 | VLAN 1       | 64.100.1.2/29      | 64.100.1.1              |
| **S2**                                 | VLAN 1       | 192.168.1.2/24     | 192.168.1.1             |
| **S3**                                 | VLAN 1       | 209.165.202.130/27 | 209.165.202.129         |
| **S4**                                 | VLAN 1       | 172.16.2.2/24      | 172.16.2.1              |
| **DNS/Web Server**                     | NIC          | 209.165.202.131/27 | 209.165.202.129         |
| **PC-A**                               | NIC          | 64.100.1.5/29      | 64.100.1.1              |
| **PC-B**                               | NIC          | 192.168.1.5/24     | 192.168.1.1             |
| **PC-C**                               | NIC          | 172.16.2.5/24      | 172.16.2.1              |

## 🛠️ Instrucciones del Examen

### Part 1: Place Devices in Proper Locations and Connect them with Proper Cables

#### Step 1: Place devices in proper Locations inside the main wiring closet

- [x] Organizar el rack para facilitar la configuración. Colocar R1, R2, S1, S2, S3 y S4 de arriba hacia abajo, dejando espacio entre los dispositivos. ✅ 2026-06-26
    
- [x] Arrastrar dos routers 4331, R1 y R2, desde el estante (shelf) hacia el rack. ✅ 2026-06-26
    
- [x] Arrastrar cuatro switches, S1, S2, S3 y S4, desde el estante hacia el rack. ✅ 2026-06-26
    
- [x] Mover PC-C a la Mesa 1 (Table1), a la izquierda, y colocarla en el área izquierda de la mesa. ✅ 2026-06-26
    
- [x] Mover el servidor DNS a la Mesa 1 (Table1), a la izquierda, y colocarlo en el área derecha de la mesa. ✅ 2026-06-26
    
- [x] Mover PC-A a la Mesa 2 (Table2), a la derecha, y colocarla en el área izquierda de la mesa. ✅ 2026-06-26
    
- [x] Mover PC-B a la Mesa 2 (Table2), a la derecha, y colocarla en el área derecha de la mesa. ✅ 2026-06-26
    

#### Step 2: Make sure all devices are powered on

- [x] Encender todos los dispositivos de la topología. ✅ 2026-06-26
    

#### Step 3: Connect devices according to the network topology

- [x] Utilizar el diagrama de topología lógica para conectar los dispositivos a los puertos correctos con los cables correctos. ✅ 2026-06-26
    

### Part 2: Configure Basic Devices Settings

> _Nota: Todas las configuraciones se realizan a través de una conexión directa por consola._

#### Step 1: Configure PCs with IPv4 addresses

- [x] Configurar manualmente las PCs con el direccionamiento IP completo utilizando la tabla de direccionamiento. ✅ 2026-06-26
    

#### Step 2: Configure router R1 and R2

- [x] **a. Configurar R1 y R2 con los siguientes parámetros:** ✅ 2026-06-26
    
    - [x] 1) Evitar que el router intente resolver comandos mal introducidos como nombres de dominio. ✅ 2026-06-26
        Utilizaremos: No ip domain-lookup
    - [x] 2) Configurar el nombre del router: R1 o R2. ✅ 2026-06-26
        Utilizaremos: hostname [nombre del router]
    - [x] 3) Configurar contraseña secreta cifrada para el modo EXEC privilegiado: `ciscoenpass`. ✅ 2026-06-26
        Utilizaremos: enable secret ciscoenpass
    - [x] 4) Configurar contraseña de acceso a la consola: `ciscoconpass`. ✅ 2026-06-26
        Seguiremos una pequeña secuencia de pasos, donde debemos entrar primero a la consola
        Utilizaremos: line console 0
        Luego utilizaremos: password ciscoconpass
        Al final utilizaremos: login
        Aprovecharemos y activaremos: logging synchronous
    - [x] 5) Establecer la longitud mínima de contraseña en 10 caracteres. ✅ 2026-06-26
        A pesar de que esta un poco escondido el comando, utilizaremos: security password min-length 10
    - [x] 6) Cifrar las contraseñas en texto claro. ✅ 2026-06-26
        Para encriptar utilizaremos: service password-encryption
    - [x] 7) Configurar un banner MOTD adecuado. ✅ 2026-06-26
        Utilizaremos: banner motd # banner #
        
- [x] **b. Configurar las interfaces de los routers R1 y R2 de la siguiente manera:** ✅ 2026-06-26
    Para todos será el mismo procedimiento, simplemente cambiará su IP y su mascara
    Se entra de la siguiente manera estando en el modo global: interface [range (si aplica)] [interfaz] 
    Luego que estemos dentro: ip address [ip] [mascara en bits]
    Al final en todos para cumplir con el punto numero 4, se utilizará: no shutdown
    - [x] 1) Configurar la interfaz G0/0/0 con una descripción y direccionamiento IPv4. ✅ 2026-06-26
        
    - [x] 2) Configurar la interfaz G0/0/1 con una descripción y direccionamiento IPv4. ✅ 2026-06-26
        
    - [x] 3) Configurar la interfaz G0/0/2 con una descripción y direccionamiento IPv4. ✅ 2026-06-26
        
    - [x] 4) Habilitar todas las interfaces para que estén listas para enviar y recibir tráfico. ✅ 2026-06-26
        
- [x] **c. Configurar SSH:** ✅ 2026-06-26
    
    - [x] 1) Configurar el nombre de dominio: `ccna-lab.com`. ✅ 2026-06-26
        Sencillamente utilizaremos el comando: ip domain-name ccna-lab.com
    - [x] 2) Crear un usuario administrativo en la base de datos local: ✅ 2026-06-26
        
        - **Username:** `admin`
        - **Secret Password:** `admin1pass`
		Utilizaremos: username **admin** privilege 15 secret **admin1pass**

    - [x] 3) Configurar el inicio de sesión (login) en las líneas VTY para usar la base de datos local. ✅ 2026-06-26
        Para utilizar la bd es necesario el paso anterior, entonces una vez que sepamos eso, procedemos a ingresar el siguiente comando: line vty 0 15 
        Luego utilizaremos: login local
        Con esto ya utilizara el usuario creado
        Aprovecharemos para activar loggin synchronous en ambos routers.
    - [x] 4) Configurar las líneas VTY para aceptar únicamente conexiones SSH. ✅ 2026-06-26
        Dentro de las lineas vty, se utilizará: transport input ssh
    - [x] 5) Generar una clave criptográfica RSA con un módulo de 1024 bits. ✅ 2026-06-26
        Para generar la clave debemos estar en el modo global y utilizar:  crypto key generate rsa
        Y elegiremos 1024
    - [x] 6) Habilitar SSH utilizando la versión 2. ✅ 2026-06-26
        Se habilita estando en la configuración global con el comando: ip ssh version 2

#### Step 3: Configure switches S1, S2, S3, and S4

- [x] **a.** Configurar el hostname de acuerdo con la Tabla de Direccionamiento. ✅ 2026-06-26
    Se repetirá el mismo paso que en los routers: hostname [nombre del dispositivo]
- [x] **b.** Configurar la Interfaz de Administración (SVI) para la VLAN 1: Establecer la dirección IPv4 y activar la interfaz. ✅ 2026-06-26
    Para configurar la interfaz es:
    interfaz vlan [administrativa] `
    luego ingresamos la IP y mascara: 192.168.1.2 255.255.255.0 <-[Ejemplo]
- [x] **c.** Configurar el gateway por defecto. ✅ 2026-06-26
    Se configura en el modo global con el comando: 

### Part 3: Configure Single Area OSPFv2

#### Step 1: Configure single-area OSPF routing

- [x] **a.** Configurar el proceso de enrutamiento OSPF utilizando el ID de proceso 1. ✅ 2026-06-26
    Utilizamos: router ospf 1
- [x] **b.** Configurar manualmente el ID del router (Router ID): Usar `0.0.0.1` para R1 y `0.0.0.2` para R2. ✅ 2026-06-26
    
- [x] **c.** Configurar las declaraciones de red (network statements) para las redes adecuadas en R1 y R2 en el siguiente orden estricto: ✅ 2026-06-26
    
    - **En R1:**
        
        - [x] 1. La red de la interfaz G0/0/2 ✅ 2026-06-26
            
        - [x] 2. La red de la interfaz G0/0/0 ✅ 2026-06-26
            
    - **En R2:**
        
        - [x] 1. La red de la interfaz G0/0/2 ✅ 2026-06-26
            
        - [x] 2. La red de la interfaz G0/0/0 ✅ 2026-06-26
            
Se utilizó area 0 para todos, se siguió: network [ip de la red]  [wildcard] area [numero area]
#### Step 2: Adjust OSPF operation

- [x] **a.** Configurar las interfaces correspondientes como pasivas para no reenviar actualizaciones de OSPF donde no se requieran. ✅ 2026-06-26
    
- [x] **b.** Configurar el ancho de banda de referencia: Ajustar el ancho de banda de referencia a 1 Gigabit. ✅ 2026-06-26
    Utilizamos: auto-cost reference-bandwidth [gb en mb]
- [x] **c.** Configurar la red OSPF como una red punto a punto (point-to-point). ✅ 2026-06-26
    Nos dirigimos a la interfaz a la que le debemos poner la configuración, en este caso será el G0/0/0
    Pondremos: ip ospf network point-to-point
- [x] **d.** Configurar el tiempo de saludo (hello time) en 30 segundos. ✅ 2026-06-26
    Dentro de la misma interfaz pondremos: ip ospf hello-interval [intervalo], luego configuramos el dead-interval: ip ospf dead-interval [intervalo del hello x4]

### Part 4: Configure Access Control and NAT

#### Step 1: Verify connectivity

- [x] Verificar que PC-B no pueda visitar el servidor web. ✅ 2026-06-26
    
- [x] Verificar que PC-C no pueda hacer ping a PC-A. ✅ 2026-06-26
    

#### Step 2: Configure NAT

- [x] **a.** Configurar NAT estático en el router R1 con la dirección IP pública `64.100.1.7` para permitir que PC-B acceda al servidor web. ✅ 2026-06-26
    
- [x] **b.** Configurar PAT en el router R2 para permitir que algunos dispositivos de la red conectada a la interfaz G0/0/1 accedan a internet: ✅ 2026-06-26
    
    - [x] 1) Crear un pool NAT llamado `IPNAT1` con un rango de direcciones IP de `209.165.202.140` a `209.165.202.150` con la máscara de subred `255.255.255.224`. ✅ 2026-06-26
        
    - [x] 2) Crear una ACL numerada (ACL 1) para permitir que los dispositivos con el rango de direcciones IP de `172.16.2.1` a `172.16.2.15` accedan a internet a través de NAT. ✅ 2026-06-26
        
    - [x] 3) Utilizar PAT para permitir que se comparta el rango de direcciones IP públicas. ✅ 2026-06-26
        

#### Step 3: Configure access control on R1

- [x] **a.** Crear una ACL estándar llamada `R1-VTY-LIMIT` para permitir únicamente a PC-B el acceso a las líneas VTY de R1. ✅ 2026-06-26
    
- [x] **b.** Aplicar la ACL creada. ✅ 2026-06-26
    

#### Step 4: Configure access control on S1

- [x] **a.** Crear una ACL estándar llamada `S1-VTY-LIMIT` para permitir únicamente a PC-B el acceso a las líneas VTY de S1. ✅ 2026-06-26
    
- [x] **b.** Aplicar la ACL creada. ✅ 2026-06-26
    

#### Step 5: Configure access control on R2

- [x] **a.** Crear una ACL estándar llamada `R2-VTY-LIMIT` para permitir únicamente a PC-C el acceso a las líneas VTY de R2. ✅ 2026-06-26
    
- [x] **b.** Crear una ACL extendida llamada `R2-SECURITY` para restringir el acceso desde internet cumpliendo con cuatro sentencias: ✅ 2026-06-26
    
    - [x] Permita conexiones FTP desde la dirección IP pública de PC-B hacia el servidor web/DNS. ✅ 2026-06-26
        
    - [x] Deniegue todas las demás conexiones FTP desde internet hacia las LANs de R2. ✅ 2026-06-26
        
    - [x] Deniegue todas las conexiones SSH desde internet. ✅ 2026-06-26
        
    - [x] Permita todos los demás tipos de conexiones desde internet. ✅ 2026-06-26
        
- [x] **c.** Aplicar las ACLs correspondientes. ✅ 2026-06-26
    

#### Step 6: Configure access control on S3

- [x] **a.** Crear una ACL estándar llamada `S3-VTY-LIMIT` para permitir únicamente a PC-C el acceso a las líneas VTY de S3. ✅ 2026-06-26
    
- [x] **b.** Aplicar la ACL creada. ✅ 2026-06-26
    

### Part 5: Perform Configuration Backup and IOS Update

#### Step 1: Use TFTP server to backup device configurations

- [x] **a.** Realizar una copia de seguridad (backup) de las configuraciones activas (running-config) de R1, S1 y S2 en el servidor TFTP ubicado en PC-B. ✅ 2026-06-26
    
- [x] **b.** Nombrar los archivos de configuración exactamente como: ✅ 2026-06-26
    
    - `R1-Run-Config`
        
    - `S1-Run-Config`
        
    - `S2-Run-Config`
        

#### Step 2: Use TFTP server to update/upgrade IOS software

- [x] **a.** Obtener una imagen de IOS más reciente desde el servicio TFTP en el servidor web/DNS. ✅ 2026-06-26
    
- [x] **b.** Validar la nueva versión del IOS del switch: `c2960-lanbasek9-mz.150-2.SE4.bin`. ✅ 2026-06-26
    
- [ ] **c.** Configurar S3 para que utilice esta versión más reciente de IOS después de recargar (reload).
    

## ❓ Preguntas y Secciones para Responder

> [!WARNING]
> 
> _Sección reservada para el desarrollo de respuestas y variables del estudiante._

- **R1 Name Variable:**
    
- **R2 Name Variable:**
    
- **Notas de Implementación de OSPFv2:**
    
- **Registro de NAT / Canales PAT:**
    
- **Configuración de Líneas de Control de Acceso (ACLs):**