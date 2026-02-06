# TEMA 3: Tipos de sistemas de archivos en Linux

Veremos como organiza linux los datos dentro de un disco o una memoria.
Cada sistema de archivos tiene un propósito distinto. 


1. **ext4 — El estándar de Linux**
Es el sistema de archivos más común en distribuciones como Ubuntu, Debian, Mint, etc.

Características:
- Muy estable
- Muy rápido
- Ideal para uso general
- Soporta archivos grandes
- Soporta journaling (protección ante apagones)
- Dónde se usa
- Partición /
- Partición /home
- Discos externos formateados para Linux

2.**XFS — Optimizado para rendimiento**
Usado mucho en servidores y sistemas que manejan archivos muy grandes.

Características:
- Altísimo rendimiento
- Excelente para bases de datos
- Muy eficiente con archivos grandes
- No es tan flexible como ext4 para tareas pequeñas
- Dónde se usa
- Servidores
- Sistemas de almacenamiento grandes
- Distribuciones como RHEL y CentOS lo usan por defecto

3.**Btrfs — El moderno y avanzado**
Es un sistema de archivos con funciones avanzadas.

Características:
- Snapshots
- Compresión
- Subvolúmenes
- Autocorrección de errores
- Dónde se usa
- openSUSE
- Fedora (en algunas configuraciones)
- Sistemas que necesitan snapshots tipo “Time Machine”
Es más complejo, pero muy potente.

4. **tmpfs — Vive en la RAM**
Este sistema de archivos no está en el disco, sino en la memoria RAM.

Características:
- Súper rápido
- Temporal
- Se borra al reiniciar
- Dónde se usa
- `/tmp`
- `/run`
- `/dev/shm`
- Ideal para datos temporales.

5. **procfs — Información del kernel**
Este no guarda archivos reales.
Es un sistema virtual que muestra información del kernel y procesos.
Ejemplos:
-` /proc/cpuinfo`
- `/proc/meminfo`
- `/proc/1 (systemd)`
Es como una ventana al interior del sistema.

6. **sysfs — Información del hardware**
Otro sistema virtual, más moderno que procfs.
Ejemplos:
- `/sys/class/net →` interfaces de red
- `/sys/block →` discos
- `/sys/devices →` hardware detectado
- Es la forma en que el kernel expone el hardware al sistema.

## Resumen

- **ext4   →**estándar, estable, uso general
- **xfs    →**rendimiento, archivos grandes
- **btrfs  →**snapshots, compresión, moderno
- **tmpfs  →**vive en RAM, temporal
- **procfs →**info del kernel y procesos
- **sysfs  →** info del hardware


