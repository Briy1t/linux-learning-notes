Linux Permissions Toolkit — Bloque 1
Creación inicial del proyecto, primer script y resolución de incidencias reales.

# Objetivo del Bloque 1

Documentar la creación del proyecto, la estrucutura inicial, el primer script (create_user.sh) y las incidencias encontradas durante el proceso.

--------------------------------------

### Creacion del primer script: create_user.sh

- Pasos realizados
 1. Verificar en qué usuario estoy trabajando con `pwd`
 2. Crear el directorio principal del proyecto 
 3. Crear la carpeta scripts/
 4. Crear el archivo del script con `touch`

### Script funcional: create_user.sh

-¿Qué hace?
 1. Verifica si se ha pasado un nombre de usuario como argumento
 2. Crea el usuario con su directorio home
 3. Solicita la contraseña del nuevo usuario
 4. Añade el usuario al grupo linuxteam
 5. Muestra un mensaje de confirmación
 6. Editarlo con `nano`

 ## Codigo

 #!/bin/bash

# Usage: ./create_user.sh username

USER=$1

if [ -z "$USER" ]; then
    echo "Usage: $0 username"
    exit 1
fi

sudo useradd -m "$USER"
sudo passwd "$USER"
sudo usermod -aG linuxteam "$USER"

echo "USER $USER created and added to linuxteam."

## Evidencias 

![Script_user+group](images/script_add,save_NEWusers.png)

----------------------------------

 7. Probarlo y verificar que dunciona correctamente

### Evidencias 

![Creacion_directorio l](images/linux_permi_creacion_de_directorio.png)

------------------------------

## Incidencia 1: Distribución de teclado incorrecta en Ubuntu (VirtualBox)

- Problema
Las teclas ñ, €, ¿, ¡, ', ? no coincidían con el teclado físico español.

- Causa
Ubuntu estaba usando la distribución English (US) por defecto.

Solución aplicada
Abrir Configuración → Teclado

Añadir “Spanish (no dead keys)”
Eliminar “English (US)”

Reiniciar la máquina virtua

### Evidencias 

![Incidencia de teclado](images/incidencia_con_el_teclado.png)



-----------------------------

## Incidencia 2: “Permission denied” al acceder a /home de otro usuario

-Problema
El usuario briyit no podía acceder al directorio /home/carlos2.

-Causa
Linux protege la privacidad de cada usuario.
Solo el dueño del directorio o root puede acceder al home de otro usuario.

Solución aplicada
Verificar permisos con:

bash
ls -ld /home/carlos2
Interpretación del resultado:

drwx------ → solo el dueño puede entrar

El usuario actual no tiene permisos de lectura ni ejecución

### Evidencia 

![Error de permisos](images/incidencia_denied.png)

-------------------

# Comandos usados
## Navegación y directorios
pwd                 # Muestra el directorio actual
mkdir nombre        # Crea un nuevo directorio
cd nombre           # Entra en un directorio

## Archivos y scripts
touch archivo.sh    # Crea un archivo vacío
nano archivo.sh     # Abre el archivo en el editor nano
chmod +x archivo.sh # Da permisos de ejecución al script

## Usuarios, grupos y permisos
ls -ld ruta         # Muestra permisos y dueño de un directorio
id                  # Muestra UID y grupos del usuario actual
getent passwd       # Lista todos los usuarios del sistema
getent group        # Lista todos los grupos del sistema

## Aprendizaje del bloque 1
- Comprensión de la jerarquía de usuarios en Linux
- Creación de scripts funcionales con validación
- Manejo de incidencias reales en entorno virtual
- Documentación técnica con Markdown y evidencias




