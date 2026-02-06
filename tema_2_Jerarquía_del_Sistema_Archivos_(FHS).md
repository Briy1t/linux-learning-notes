# TEMA 2 — Jerarquía del Sistema de Archivos (FHS)
(Filesystem Hierarchy Standard)

# / — La raíz del sistema
Es el “piso cero”.
Todo cuelga de aquí.
Ejemplo:
- /home
- /etc
- /var
- /usr

# /home — Las carpetas de los usuarios
Aquí vive tu usuario:
- /home/briyit
- Tus documentos
- Tus descargas
- Tu escritorio
- Es lo más parecido a “Mis Documentos” en Windows.

# /root — El home del usuario root
No confundir con /.
Es la carpeta personal del superusuario.

# /etc — Configuración del sistema
Aquí viven todos los archivos de configuración.
Ejemplos:
- /etc/passwd → usuarios
- /etc/shadow → contraseñas
- /etc/ssh/sshd_config → configuración de SSH
- /etc/fstab → montaje de discos
Si quieres cambiar cómo funciona algo → está en /etc.

# /var — Datos que cambian (variable)
Aquí vive todo lo que crece, cambia o se actualiza.
Ejemplos:
- /var/log → logs del sistema
- /var/www → páginas web
- /var/spool → colas de impresión, correo
Piensa en /var como “lo que se mueve”.

# /usr — Programas y librerías del sistema
Aquí está la mayoría del software instalado.
Ejemplos:
- /usr/bin → comandos
- /usr/sbin → comandos administrativos
- /usr/lib → librerías
- /usr/share → documentación, iconos, plantillas
 /usr no significa “usuario”, sino “Unix System Resources”.
 
# /bin y /sbin — Comandos esenciales
Son los comandos que el sistema necesita incluso en modo de rescate.
Ejemplos:
- /bin/ls
- /bin/cp
- /sbin/reboot
- /sbin/mkfs

# /tmp — Archivos temporales
Aquí se guardan archivos que se borran solos.

Programas que necesitan guardar algo rápido.

# /dev — Dispositivos
Aquí viven los dispositivos representados como archivos.
Ejemplos:
- /dev/sda → disco
- /dev/tty → terminal
- /dev/null → agujero negro
Linux trata TODO como archivos, incluso el hardware.

# /proc — Información del kernel y procesos
Es un sistema de archivos virtual.
Ejemplos:
- /proc/cpuinfo
- /proc/meminfo
- /proc/1 → información del proceso PID 1 (systemd)
- 
# /sys — Información del hardware
Otro sistema virtual, más moderno que /proc.

``` text
/
├── home      → usuarios
├── root      → usuario root
├── etc       → configuración
├── var       → datos que cambian
├── usr       → programas y librerías
├── bin       → comandos esenciales
├── sbin      → comandos administrativos
├── tmp       → temporales
├── dev       → dispositivos
├── proc      → info del kernel y procesos
└── sys       → info del hardware
```

| **Carpeta** | **Función** |
|:--|:--|
|/ |raíz del sistema|
|/home |usuarios normales|
|/root|usuario root |
|/etc|configuraciones|
|/var|datos que cambian (logs, bases)|
|/usr | programas del sistema |
|/bin |comandos esenciales |
|/sbin |comandos de admin |
|/tmp |archivos temporales |
|/opt |software externo |
|/media |USB y discos |
|/mnt |montajes manuales |






laboratorio practico 

Escribir en la terminal 

```bash

ls /usr
```

![ls /usr](imagenes/ls_usr.png)




Este contenido puede variar según la distribución y los paquetes instalados.
La estructura de /usr refleja la organización del software del sistema.
Es una de las carpetas más importantes del FHS (Filesystem Hierarchy Standard).


Interpretación: - `bin/` → programas del sistema - `lib*/` → librerías - `share/` → documentación, iconos, plantillas - `local/` → programas instalados manualmente







