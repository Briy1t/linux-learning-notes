# Administración básica de usuarios y permisos
Ejercicio práctico de Linux — Gestión de usuarios, grupos y permisos

## Objetivo del ejercicio
Demostrar dominio de:
-Creación de usuarios
-Creación de grupos
-Gestión de permisos
-Navegación en el sistema
-Comandos administrativos

## Resolución de errores reales

## Preparación del entorno
Abrimos la terminal:
---
bash
Ctrl + Alt + T
Verificamos el usuario actual:
---
bash
whoami
Cambiamos al usuario destinado para ejercicios:
---
bash
su - ejercicios
Verificamos que el cambio fue exitoso:
---

bash
whoami
[Aquí puedes insertar tu primera imagen]

## Creación del grupo devteam
Creamos el grupo solicitado:

bash
sudo groupadd devteam
Verificamos que el grupo existe:

bash
getent group devteam
[Imagen opcional aquí]

### Creación del usuario ana
Creamos el usuario:

bash
sudo useradd ana
Asignamos contraseña:

bash
sudo passwd ana
Verificamos si tiene carpeta personal:
---
bash
ls -ld /home/ana
 Error detectado: usuario sin carpeta personal
El usuario fue creado sin la opción -m, por lo que no se generó /home/ana.

### Corrección del error: crear la carpeta personal
Creamos manualmente la carpeta:

bash
sudo mkdir /home/ana
sudo chown ana:ana /home/ana
Verificamos:

bash
ls -ld /home/ana
[Imagen opcional aquí]

## Añadir el usuario al grupo devteam
bash
sudo usermod -aG devteam ana
Verificamos:

bash
id ana
getent group devteam
[Imagen opcional aquí]

## Crear archivo compartido en /opt
Creamos el archivo:

bash
sudo touch /opt/devteam_notes.txt
Verificamos propietario y permisos:

bash
ls -l /opt/devteam_notes.txt
## Asignar propietario y grupo correctos
bash
sudo chown root:devteam /opt/devteam_notes.txt
Asignamos permisos 660:

bash
sudo chmod 660 /opt/devteam_notes.txt
Verificamos:

bash
ls -l /opt/devteam_notes.txt
Resultado esperado:

Código
-rw-rw---- 1 root devteam ...
[Imagen opcional aquí]

## Probar acceso como ana
Entramos como el usuario:

bash
sudo -u ana -i
Intentamos escribir en el archivo:

bash
echo "texto de prueba" >> /opt/devteam_notes.txt
Leemos el archivo:

bash
cat /opt/devteam_notes.txt
Si aparece el texto, el ejercicio está completado correctamente.

[Imagen opcional aquí]

## Comandos nuevos aprendidos

echo
Escribe texto en pantalla o en archivos.

bash
echo "Hola mundo"
echo "texto" >> archivo.txt
---
cat
Muestra el contenido de un archivo.

bash
cat archivo.txt
✅ Resultado final
El usuario ana existe
---
Su carpeta personal /home/ana está creada y asignada correctamente

El grupo devteam existe

El archivo /opt/devteam_notes.txt pertenece a root:devteam

Tiene permisos 660

El usuario ana puede escribir en él

