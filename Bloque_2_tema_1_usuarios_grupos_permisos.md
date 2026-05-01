# BLOQUE 2 — TEMA 1: Usuarios, Grupos y Permisos en Linux
Linux es un sistema multiusuario, todo lo que ocurre depende de:
- Quién ejecuta un comando
- Qué permisos tiene
- A qué grupo pertenece
- Qué privilegios puede elevar
---
Este tema cubre desde permisos básicos hasta permisos especiales y ACLs.
---
##  1. Usuarios en Linux
Un usuario es una identidad dentro del sistema.
- Cada usuario tiene:
  - nombre
  - UID (User ID)
  - grupo principal
  - grupos secundarios
  - directorio home
  - shell
  - permisos asociados
---
## 2. Grupos en Linux
Un grupo es un conjunto de usuarios que comparten permisos.Ejemplos típicos:

- Grupo	Función
- sudo	usuarios que pueden usar sudo
- www-data
- usuarios del servidor web
- docker
- usuarios que pueden usar Docker sin sudo
---
- Ejercicio practico: [Usuarios_Grupos]( Usuarios_Grupos_Linux.md)
## 3. Archivos importantes del sistema
- `/etc/passwd `— Información de usuarios

```text

usuario:x:UID:GID:comentario:/home/usuario:/bin/bash

```
- `/etc/shadow `— Contraseñas encriptadas. Solo root puede leerlo.

**Ejemplo:**
```text
briyit:$6$kjsdfh8H...:19876:0:99999:7:::
```
- `/etc/group` — Grupos del sistema

```text
grupo:x:GID:miembros
```

## 4. Tipos de usuarios
- Tipo	UID	Descripción
- root	0	administrador total
- usuarios del sistema	1–999	servicios (www-data, mysql…)
- usuarios normales	1000+	los que tú creas
  
## 5. Tipos de grupos
- Grupo principal → el grupo por defecto del usuario
- Grupos secundarios → permisos adicionales

```text
uid=1001(briyit) gid=1001(briyit) groups=1001(briyit),27(sudo),1002(docker)
```

###  Comandos esenciales

| Comando	| Función |
|---------|-----------|
|id|	ver UID, GID y grupos|
|whoami|	ver usuario actual|
|groups|	ver grupos|
|useradd	|crear usuario|
|usermod	|modificar usuario|
|userdel |	eliminar usuario |
|passwd |	cambiar contraseña |
| groupadd	| crear grupo |
| groupdel |	eliminar grupo |
| gpasswd |	gestionar grupos|

## Gestión de usuarios
- Crear usuario (forma correcta)
```bash
sudo useradd -m -s /bin/bash juan
```
- Asignar contraseña
```bash
sudo passwd juan
```
- Añadir a un grupo
```bash
sudo usermod -aG sudo juan
```
- Eliminar usuario + home
```bash
sudo userdel -r juan
```
### Mini‑laboratorio de grupos
- Crear grupo
- Crear usuario
- Añadir usuario al grupo
- Verificar
- Quitar del grupo
- Eliminar grupo
- Si no se elimina, puede ser porque el usuario tiene procesos activos.
Solución:

```bash
sudo pkill -u testuser
```

 - ![imagen 1](imagenes/im1.png)
 - ![imagen 2](imagenes/im2.png)
 - ![imagen 3](imagenes/im3.png)
 - ![imagen 4](imagenes/im4.png)

## Permisos en Linux
Cada archivo tiene permisos para:

  - u → usuario
  - g → grupo
  - o → otros

-Permisos:

  - r → leer
  -  w → escribir
  -  x → ejecutar


### Tipos de archivos (primer carácter)
|Símbolo	Tipo
|-	|archivo |
|d	|directorio |
|l	|enlace |
|c	|dispositivo de caracteres |
|b	|dispositivo de bloques |

###  Cambiar permisos — chmod
- **Modo simbólico**
Código
chmod u+x archivo
chmod g-w archivo
chmod a+r archivo
- **Modo numérico**
Permiso	Valor
- r	4
- w	2
- x	1

- Ejercicio administracion del sistema: [Administracion_usuarios_grupo](administracion_basica_usuarios.md)

###  Cambiar propietario — chown
- `sudo chown usuario archivo`
- `sudo chown usuario:grupo archivo`
  
## Permisos especiales

1. SUID `(u+s)` :Ejecuta el archivo con permisos del propietario.
- `chmod u+s archivo`

2. SGID `(g+s)` :En directorios: los archivos heredan el grupo.
- Muy usado en proyectos compartidos.
- `chmod g+s carpeta`
  
3. Sticky Bit `(t)` : Evita que un usuario borre archivos de otros.
-` chmod +t carpeta`

### Mini‑laboratorio de permisos especiales
- Crear carpeta
- Activar SGID
- Activar Sticky Bit
- Ver permisos
- Resultado esperado: drwxr-sr-t

 - ![imagen 5](imagenes/im5.png)

| Permiso | Símbolo | Se usa en | ¿Qué hace? |
|:--|:--|:--|:--|
|SUID |s (en user) | archivos | Ejecuta con permisos del dueño |
|SGID |s (en group) | archivos y directorios | Ejecuta con permisos del grupo / hereda grupo |
|Sticky Bit | t | directorios| Solo el dueño puede borrar sus archivos |

### TABLA EXTRA — SUID, SGID y Sticky Bit (modo numérico)

|Permiso especial	|Letra |	Valor numérico |	Qué hace	| Ejemplo comando |
|-------- |----- |------| -----------| --------|
|SUID |	s en usuario |	4 |	Ejecuta con permisos del dueño |	chmod 4755 archivo |
|SGID |	s  en grupo	 |2 |	Archivos heredan el grupo del directorio	|chmod 2770 carpeta |
|Sticky Bit |	t en otros |	1	| Solo el dueño puede borrar sus archivos |	chmod 1777 carpeta |


#### Combinaciones típicas

- 2770	SGID + permisos completos para user y group	chmod 2770 carpeta
- 3770	SGID + Sticky Bit	chmod 3770 carpeta
- 4755	SUID + permisos 755	chmod 4755 archivo
- 1777	Sticky Bit (modo /tmp)	chmod 1777 carpeta


##  ACLs — Permisos avanzados

Las ACLs permiten dar permisos granulares, usuario por usuario, sin romper la estructura de grupos.
Yo las entiendo como permisos extra que se añaden encima de los permisos normales.
No sustituyen nada: simplemente amplían.

### Comandos esenciales de ACLs
1. Dar permisos a un usuario
```bash
sudo setfacl -m u:nombre:rwx /ruta/carpeta
```
2. Dar permisos a un grupo
```bash
sudo setfacl -m g:grupo:rx /ruta/carpeta
```
3. Ver las ACLs aplicadas
```bash
getfacl /ruta/carpeta
```
4. Eliminar ACLs de un usuario
```bash
sudo setfacl -x u:nombre /ruta/carpeta
```
5. Quitar todas las ACLs
```bash
sudo setfacl -b /ruta/carpeta
```

---

Tabla resumen ACLs

| Concepto |	Qué significa| 	Ejemplo práctico	| Comando |
|---------| ----------------------------------| --------------------------------- | --------------------------------- |
|ACL	|Permisos adicionales por usuario o grupo	|Dar acceso sin meter al grupo	|setfacl -m u:briyit:r /srv/empresa/ventas|
|ACL de grupo	|Permiso específico para un grupo |	Acceso temporal a auditores	|setfacl -m g:auditores:rx|
|Máscara (mask)|	Límite máximo de permisos que pueden tener las ACLs	| Si mask es r-x, nadie tendrá w	|getfacl carpeta |
|Eliminar ACL de usuario|	Quitar permisos extra	| Revocar acceso	|setfacl -x u:maria |
|Eliminar todas las ACLs|	Dejar la carpeta limpia	|Volver a u/g/o	|setfacl -b carpeta|
|Ver ACLs|	Mostrar permisos avanzados|	Comprobar accesos|	getfacl carpeta|


### ACLs vs Grupos
| Situación |	Uso grupos	 |Uso ACLs|
|-------------| ------------ |--------------|
|Usuario pertenece al departamento	|✔️	 | | 
|Usuario necesita acceso temporal	| |	✔️ |
|Usuario necesita permisos distintos al grupo |	|	✔️|
|Estructura estable y permanente	|✔️	|  |
|Auditorías, visitas, soporte externo |		|✔️ |
|No quiero romper la seguridad del grupo	| |	✔️| 



### La máscara (mask)
Cuando aplicas ACLs, Linux crea automáticamente una mask, que es el límite máximo de permisos que pueden tener todas las ACLs (excepto el dueño).

- Ejemplo:

```bash
mask::r-x
```
Aunque yo ponga:

```bash
u:maria:rwx
```

María NO tendrá w porque la máscara lo bloquea.


- **“La máscara es el techo. Las ACLs no pueden superar ese techo.”**

### Ver la máscara
```bash
getfacl carpeta
```
### Cambiar la máscara
```bash
sudo setfacl -m m:rwx carpeta
```
- m: → mask
- rwx → permisos máximos permitidos

[Ejercicio de permisos ](Gestión_de_Identidades_Empresarial.md)
