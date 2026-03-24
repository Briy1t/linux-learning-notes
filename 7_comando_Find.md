# FIND — BÚSQUEDA AVANZADA EN LINUX
 
# 1. ¿Qué es find?
'find' -> sirve para buscar archivos, carpetas y dispositivos dentro del sistema.
- puede buscar por:
- nombre
- extensión
- tipo
- tamaño
- fecha
- permisos
- propietario
- y más

# 2. Sintaxis básica

“find /path es la ruta donde estan los archivos para ser encontrados .”
La sintaxis es:
Código
find /ruta -type tipo -name "patrón"

Ejemplos de rutas:
/ → raíz
. → carpeta actual
/home/briyit/ → ruta específica
 3. Tipos de archivo (-type)
De tu documento:
“f – Archivo regular… d – Carpeta… l – Enlace simbólico… c – Dispositivos de caracteres… b – Dispositivos de bloque.”
Los más usados:
Tipo
Significado
-type f
archivo normal
-type d
carpeta
-type l
enlace simbólico
-type c
dispositivo de caracteres
-type b
dispositivo de bloque

Ejemplo:
Código
find . -type d

Busca solo carpetas.

4. Buscar por nombre (-name)
De tu documento:
“find . -type f -name "style*"”
Ejemplos:
Archivos que empiezan por “style”
Código
find . -type f -name "style*"

Archivos .html
Código
find . -type f -name "*.html"

 Archivos ocultos
Código
find . -type f -name ".*"

 5. Buscar por tamaño (-size)
De tu documento:
“find / -size +250M”
Unidades:
G → gigas
M → megas
K → kilobytes
c → bytes
Ejemplos:
Archivos mayores de 100 MB
Código
find / -type f -size +100M

 Archivos menores de 10 KB
Código
find . -type f -size -10K

 6. Buscar por fecha (-mtime)
De tu documento:
“-mtime +10 significa que estás buscando un archivo que se modificó hace 10 días.”
Ejemplos:
 Archivos modificados hace más de 10 días
Código
find . -mtime +10

 Archivos modificados hace menos de 3 días
Código
find . -mtime -3

Archivos modificados exactamente hace 1 día
Código
find . -mtime 1

 7. Buscar carpetas
De tu documento:
“find . -type d”
Ejemplo:
Código
find /home -type d

 8. Buscar dispositivos (avanzado)
De tu documento:
“find / -type c”
“find / -type b”
Ejemplos:
Dispositivos de caracteres
Código
find /dev -type c

Dispositivos de bloque
Código
find /dev -type b

 9. EJERCICIO (solo explicación, sin comandos)
Respóndeme estas 6 preguntas para confirmar que lo entendiste:
1. ¿Qué significa -type f?
2. ¿Qué buscaría este comando?
find . -type f -name "*.conf"
3. ¿Qué unidad representa la letra M en -size +50M?
4. ¿Qué hace este comando?
find /home -type d
5. ¿Qué buscaría este comando?
find . -mtime -5
6. ¿Qué patrón usarías para buscar archivos ocultos?
¿Por qué find usa . o / después del comando?
Porque find siempre necesita un punto de inicio, es decir, desde dónde quieres que empiece a buscar.
Ese punto de inicio puede ser:
. → la carpeta actual
/ → la raíz del sistema
/home/usuario → una ruta específica
 1. ¿Qué significa el punto . en find?
El punto . significa:
 “la carpeta donde estoy ahora mismo”
Ejemplo:
Código
find . -type f

Significa:
 “Busca archivos en esta carpeta y en todas sus subcarpetas”.
 2. ¿Qué significa la barra / en find?
La barra / significa:
 “la raíz del sistema”
Es decir, el nivel más alto del sistema de archivos.
Ejemplo:
Código
find / -type f -name "*.log"

Significa:
✔ “Busca archivos .log en todo el sistema”.
⚠ Esto puede tardar mucho porque recorre todo Linux.
 3. ¿Qué significa usar una ruta específica?
Puedes decirle a find que empiece en cualquier carpeta.
Ejemplo:
Código
find /home/briyit -type f -name "*.txt"

Significa:
✔ “Busca archivos .txt dentro de /home/briyit”.
 RESUMEN CLARO
Símbolo
Significado
Cuándo usarlo
.
carpeta actual
cuando quieres buscar solo en donde estás
/
raíz del sistema
cuando quieres buscar en TODO Linux
/ruta/
carpeta específica
cuando sabes dónde buscar

 EJEMPLOS PARA QUE LO VEAS CLARO
Buscar archivos .html en la carpeta actual
Código
find . -type f -name "*.html"

Buscar carpetas en todo el sistema
Código
find / -type d

 Buscar archivos ocultos en tu carpeta personal
Código
find /home/briyit -type f -name ".*"
perdinete por terminar
