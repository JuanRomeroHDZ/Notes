# 🛠️ Guía Práctica de Plugins Comunitarios para Ingeniería

Esta guía contiene el uso **100% práctico y libre de teoría** para exprimir los plugins instalados. El objetivo es automatizar el flujo de trabajo, reducir clics y mantener el control visual de los laboratorios.

---

## 📅 1. Gestión del Tiempo y Bitácora Diaria

### 📌 Periodic Notes + Calendar
*¿Para qué sirve?* Te quita la fricción de pensar dónde anotar las cosas. Automatiza la creación de una **bitácora diaria** para registrar comandos, errores solucionados o avances de la tesis. El calendario te da el acceso visual a esos días.

* **Flujo Práctico:**
    1. Presiona tu atajo de nota diaria (ej. `Alt + D`).
    2. Usa esa nota como tu terminal de texto del día: todo lo que configures en Cisco, Proxmox o Wazuh hoy, se queda ahí anotado cronológicamente.
* **Checklist de Uso:**
    * [ ] Haz clic en cualquier día del panel visual de **Calendar** para ver qué comandos usaste ese día exacto.
    * [ ] Usa la nota diaria para anotar errores de Packet Tracer (como desajustes de duplex) y cómo los solucionaste para que no se te vuelvan a olvidar.



### 🎯 Tasks
*¿Para qué sirve?* Centraliza todos tus pendientes dispersos en el Vault sin que tengas que buscarlos nota por nota.

* **Flujo Práctico:** En cualquier nota de laboratorio, escribe un pendiente usando `- [ ]` y añade el formato de Tasks con `#task`.
* **Sintaxis Útil:**
    ```markdown
    - [ ] Reconstruir EtherChannel en grupo 2 de MSW-1 📅 2026-06-25 #task
    ```
* **Checklist de Uso:**
    * [ ] Usa el comando `Tasks: Create or edit task` (`Ctrl + P`) para añadir prioridades o fechas límite visualmente.

---

## 📊 2. Automatización e Interfaces Visuales

### 🧊 Commander
*¿Para qué sirve?* Eres usuario de Linux; te gustan los accesos directos. Este plugin te permite poner botones personalizados en cualquier parte de la interfaz (barra lateral, barra de estado, notas).

* **Flujo Práctico:** Crea un botón permanente en la barra lateral izquierda que ejecute comandos frecuentes con un solo clic.
* **Checklist de Uso:**
    * [ ] Agrega un botón con el ícono de un "Checkmark" para abrir la lista de tareas pendientes global.
    * [ ] Agrega un botón con el ícono de una "Terminal" para crear instantáneamente una nota de laboratorio formateada.

### 🎨 Excalidraw
*¿Para qué sirve?* Tu herramienta principal por ser visual. Permite dibujar esquemas, topologías y flujos de datos directamente dentro de Obsidian.

* **Flujo Práctico:** No expliques una red con texto; dibújala en un lienzo de Excalidraw e incrústala en tus notas técnicas.
* **Checklist de Uso:**
    * [ ] Modela la topología de red de tus prácticas (Routers, Switches, VLANs).
    * [ ] Mapea con flechas el flujo de logs desde los agentes hacia el Server de Wazuh para entender tu tesis de un solo vistazo.

---

## 🖥️ 3. Datos, Consultas y Código

### 🦅 Dataview
*¿Para qué sirve?* Transforma tus notas en una base de datos interactiva. Crea tablas de control automáticas para que las notas te busquen a ti.

* **Bloque de Código Práctico (Copia y pega en tu nota de inicio/dashboard):**
    ```dataview
    TABLE file.folder as "Ubicación", file.mday as "Última Modificación"
    FROM #laboratorio o #tesis
    SORT file.mday DESC
    LIMIT 10
    ```
* **Checklist de Uso:**
    * [ ] Agrega la etiqueta `#laboratorio` a tus notas de Packet Tracer.
    * [ ] Revisa tu nota de inicio; Dataview listará automáticamente tus últimos laboratorios sin que tengas que indexarlos a mano.

### 📝 Advanced Tables
*¿Para qué sirve?* En redes, las tablas de direccionamiento IP son obligatorias, pero el Markdown normal es un dolor de cabeza para editarlas. Este plugin te da el control de un "Mini-Excel".

* **Flujo Práctico:** Al escribir `| IP | Interfaz |` y presionar `Enter`, el plugin construye el formato de tabla solo.
* **Teclas Rápidas:**
    * `Tab`: Avanzar a la siguiente celda (y auto-alinear visualmente las columnas).
    * `Enter`: Crear una nueva fila abajo.
* **Checklist de Uso:**
    * [ ] Diseña tus tablas de subredes IPv4/IPv6 usando `Tab` para mantener las máscaras y gateways perfectamente alineados.

---

## 📂 4. Control de Versiones y Estética

### 🐙 Git
*¿Para qué sirve?* Seguridad total de tu infraestructura de notas. Respalda todo tu Vault en GitHub de forma automática y silenciosa.

* **Flujo Práctico:** Olvídate de los comandos `git add` y `git commit` en la terminal de Debian; el plugin lo hace en segundo plano mientras tú estudias.
* **Checklist de Uso:**
    * [ ] Abre los ajustes del plugin y define un `Vault Backup Interval` (ej. cada 20 o 30 minutos).
    * [ ] Duerme tranquilo sabiendo que si rompes una nota o un Canvas, puedes recuperar versiones anteriores con el historial de Git.

### 🔮 Iconize
*¿Para qué sirve?* Organización visual instantánea para el explorador de archivos de la barra izquierda.

* **Flujo Práctico:** Asigna íconos de color a tus carpetas principales para identificarlas sin necesidad de leer los nombres.
* **Checklist de Uso:**
    * [ ] Icono de un ⚙️ o 💻 para la carpeta de configuraciones de red.
    * [ ] Icono de un 📜 o 🎓 para la carpeta de la tesis.