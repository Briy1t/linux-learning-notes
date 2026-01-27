# Comandos esenciales de Linux

Este documento reúne los comandos más importantes que utilizo durante mi preparación para Linux+.  
Se irá ampliando a medida que avance en mi aprendizaje.

---

## Navegación básica
- `pwd` : Muestra la ruta actual
- `ls` : Lista archivos
- `ls -l` : Lista con permisos y detalles
- `cd ruta` : Cambia de directorio
- `cd ..` : Sube un nivel
- `cd ~` : Ir al home del usuario
- `ls -l /ruta/archivo.txt` : Verificar permisos, propietario, grupo y tamaño del archivo

---

## Crear archivos y carpetas
- `mkdir nombre` : Crear carpeta
- `mkdir -p ruta/otra` : Crear carpetas anidadas
- `touch archivo` : Crear archivo vacío
- `rm archivo` : Eliminar archivo
- `rm -r carpeta` : Eliminar carpeta y contenido
- sudo touch /ruta/archivo.txt : Crear un archivo vacío en una ruta protegida (requiere permisos de root)


---

## Gestión de usuarios
- `sudo adduser nombre` : Crear usuario con carpeta personal
- `sudo passwd nombre` : Asignar contraseña
- `id nombre` : Ver UID, GID y grupos
- `sudo userdel nombre` : Eliminar usuario
- `cambiar de usuario` : su - nombre_usuario
- `sudo useradd .m nombre` :crear un usuario con su carpeta
- `sudo -u nombre_usuario -i`: Abre una sesión como un usuario específico sin requerir contraseña



---

## Gestión de grupos
- `sudo groupadd nombre` : Crear grupo
- `sudo usermod -aG grupo usuario` : Añadir usuario a un grupo
- `getent group grupo_name` : Ver miembros del grupo
- `getent group nombre` : Ver si el grupo se creo 
- sudo chgrp grupo archivo → Cambiar solo el grupo de un archivo o directorio


---

## Permisos (modo simbólico)
- `chmod u+r archivo` :Añadir lectura al usuario
- `chmod g+w archivo` : Añadir escritura al grupo
- `chmod o-r archivo` : Quitar lectura a otros
- `chmod u=rwx,g=rx,o= archivo` : Establecer permisos exactos

---

## Permisos (modo numérico)
- `chmod 755 archivo`  
  - usuario: rwx (7)  
  - grupo: r-x (5)  
  - otros: r-x (5)

- `chmod 660 archivo`  
  - usuario: rw- (6)  
  - grupo: rw- (6)  
  - otros: --- (0)

---

## Propietarios
- `sudo chown usuario archivo` :Cambiar propietario
- `sudo chown usuario:grupo archivo` : Cambiar propietario y grupo
- `sudo chgrp grupo archivo` : Cambiar solo el grupo
-  sudo chmod 660 /ruta/archivo.txt :Asignar permisos: lectura/escritura para propietario y grupo,con ruta especifica
- sudo chown usuario:grupo archivo : Cambiar propietario y grupo al mismo tiempo


---

## Comandos administrativos
- `sudo` → Ejecutar como root
- `sudo su` → Cambiar a root
- `sudo systemctl status servicio` → Ver estado de un servicio
- `journalctl -xe` → Ver logs del sistema

- which usermod :Mostrar la ruta del ejecutable usermod
- sudo usermod -d /ruta/home -m usuario : Asignar o corregir el directorio personal de un usuario
- sudo mkdir /ruta/home : Crear manualmente un directorio personal
- sudo chown usuario:grupo /ruta/home : Asignar propiedad del directorio personal al usuario y su grupo
- ls -ld /ruta/home : Verificar permisos, propietario y grupo del directorio sin listar su contenido


---

## Comandos de red (básicos)
- `ip a` → Mostrar interfaces
- `ping host` → Comprobar conectividad
- `curl url` → Hacer petición HTTP

------


###  Comandos para escribir y leer archivos

- `echo` :Escribir texto en archivos
- `echo "Texto" >> /ruta/archivo.txt` : Añadir una línea de texto al final del archivo sin abrir editores

- `cat` : Mostrar contenido de archivos
- `cat /ruta/archivo.txt` :Mostrar el contenido completo del archivo en la terminal
- `cat /directorio/documento`


---

##  Notas
Este archivo se actualizará continuamente conforme avance en mi preparación para Linux+.
