# Linux+ Study Kit

Este repositorio reúne mis notas, comandos, ejercicios y documentación práctica  
durante mi preparación para la certificación **CompTIA Linux+**.

Incluye apuntes organizados por temas, ejemplos reales, scripts sencillos y  
problemas que he resuelto en mi entorno Linux mientras estudio de forma autodidacta.

---

## Contenido del repositorio

  ## Bloque 1 :
  **Temas**
  
  **1. Fundamentos :**
  Fundamentos esenciales de GNU/Linux: arquitectura interna, diferencia entre kernel y espacio de usuario, módulos del kernel,   proceso completo de arranque (BIOS/UEFI → GRUB → kernel → systemd → servicios → login    → shell) y conceptos clave como       terminal,       shell y servicios del sistema. Incluye comandos básicos para inspeccionar kernel, módulos y systemd.

  [Fundamentos](Bloque1_Fundamentos_Sistema.md)

  **2. Jerarquia del sistema (FHS) :**
  - Función de las carpetas principales (/, /home, /etc, /var, /usr, /bin, /sbin, /tmp, /dev, /proc, /sys).
  - Árbol visual de la estructura.
  - Tabla rápida de cada directorio.
  - Mini laboratorio usando ls /usr.

  [jerarquia_FHS](tema_2_Jerarquía_del_Sistema_Archivos_(FHS).md)

  **3. Sistema de archivos en Linux :**
  Este tema presenta los principales sistemas de archivos usados en Linux:
  ext4, XFS, Btrfs, tmpfs, procfs, sysfs
  
  [Sistema de archivos en Linux](Tema3_tipos_sistemas_de_archivos_en_linux.md)

  **4. Rutas, Navegación y PATH :**
  Explicación de rutas absolutas y relativas en Linux, cómo el sistema encuentra los comandos       mediante la variable PATH y el     orden de búsqueda (comandos internos, alias, ./, directorios   del PATH). Incluye el concepto de ./, el uso del shebang                  (#!/bin/bash, etc.), cómo       convertir un script en comando del sistema y buenas prácticas para organizar scripts en           directorios como /usr/local/bin y ~/bin.

  [Rutas, Navegación y PATH](tema4_Rutas_Navegación_y_PATH.md)

  **5. Comandos esenciales :**
  reúne los comandos esenciales de Linux para trabajar con el sistema: navegación con pwd, cd y ls; gestión de archivos mediante mkdir, touch, cp, mv y rm; lectura con cat, head, tail y less; búsqueda con           grep y sus opciones; y el uso de redirecciones y pipes   para controlar el flujo de datos. Incluye comandos de filtrado como wc, sort y uniq, además de expresiones regulares básicas con grep -E para                 búsquedas más potentes. También incorpora ejercicios prácticos para aplicar todo lo aprendido de forma           progresiva.
  
       1. Comandos de navegación
       2.  Comandos de archivos y directorios
       3.  Comandos de lectura de archivos
       4.  Comandos de búsqueda
       5.  Redirecciones y pipes  / 5.1 Comandos de filtrado y ordenación
       6.  Expresiones regulares (regex)
            
  - aqui temas 1, 2 ,3  [Comandos esenciales 1 2 3 ](Tema_5_Comandos_esenciales_1,2,3.md)
  - aqui temas 4, 5 ,6  [Comandos esenciales 4 5 6 ](TTema_5_Comandos_esenciales_4_5_6.md)
        

  ## Bloque 2 :
  Administración del Sistema Linux reúne los fundamentos esenciales para trabajar como SysAdmin. Incluye la gestión completa de usuarios, grupos y permisos, desde rwx hasta permisos especiales y ACLs. También abarca el control de procesos y servicios mediante             herramientas como ps, top, systemctl y journalctl. Se profundiza en la instalación y mantenimiento de software, redes básicas, configuración de interfaces, firewall y diagnóstico. Además, se estudia el almacenamiento: particiones, sistemas de archivos, montajes y       LVM. Finalmente, se trabaja con logs del sistema y monitorización básica para detectar errores, analizar eventos y mantener la estabilidad del sistema. Estara dividido en temas.
  
  **1. Usuarios, Grupos y Permisos en Linux**:
  Introduce la gestión de usuarios, grupos y permisos en Linux. Explica archivos clave del sistema, comandos para administrar identidades, permisos básicos y avanzados, propietarios, grupos y permisos especiales como SUID, SGID y Sticky Bit. También incluye ACLs y        conceptos de sudoers para controlar privilegios de forma granular.
  
  [Usuarios, Grupos y Permisos en Linux](Bloque_2_tema_1_usuarios_grupos_permisos.md)

  
  


  --- 
   -  **Otros**
  
  - - **Comandos esenciales lista general**  
  Explicaciones y ejemplos de uso de los comandos más utilizados en administración Linux.

  [Comandos_esenciales](Comandos%20esenciales%20de%20Linux.md)

- **Permisos y ownership**  
  Notas sobre `chmod`, `chown`, `umask`, ACLs y casos reales.

- **Scripting en Bash**  
  Scripts simples creados durante mi aprendizaje.

- **Networking básico**  
  Comandos de red, diagnóstico y configuración inicial.

- **Troubleshooting**  
  Errores reales que he encontrado y cómo los resolví.

- **Notas para el examen Linux+**  
  Resúmenes, conceptos clave y recordatorios importantes.

---

##  Objetivo del repositorio

Este proyecto forma parte de mi formación autodidacta en administración de sistemas Linux.  
Mi objetivo es documentar todo mi proceso de estudio, crear mis propias herramientas  
y consolidar conocimientos de cara a la certificación **Linux+**.

---

## Sobre mí

Soy Briyit, estudiante de administración de sistemas, scripting y cloud computing.  
Este repositorio refleja mi progreso real, mis prácticas y mi camino hacia la certificación Linux+.

# linux-learning-notes
Repositorio de estudio con comandos, notas y ejercicios para la certificación Linux+.
