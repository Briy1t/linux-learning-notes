# Creación de un script de backup con Bash y mejora mediante rsync
## 1. Objetivo 
Mi intención era automatizar la copia de una carpeta de
trabajo hacia una carpeta de respaldo local. Para ello decidí crear
un script en Bash que ejecutara el proceso de forma sencilla. Durante la prueba
detecté un problema de eficiencia y lo corregí utilizando rsync, que es la herramienta
adecuada en entornos profesionales y cloud.

## 2. Creación del archivo del script
Primero generé el archivo donde escribiría el código del backup:

```bash
touch mibackups.sh
```
Después lo abrí con el editor:

```bash
nano mibackups.sh
```

- !()[imagenes/a1.png]
  
## 3. Contenido inicial del script
Dentro del archivo escribí el siguiente código:

```bash
#!/bin/bash

# Definimos variables para que sea fácil de cambiar después
ORIGEN="./proyectos"
DESTINO="./backups"

# 1. Verificamos si la carpeta de backup existe, si no, la creamos
if [ ! -d "$DESTINO" ]; then
    mkdir -p "$DESTINO"
    echo "Carpeta de backup creada."
fi

# 2. Copiamos todo de forma recursiva y "verbose" (-v para ver qué pasa)
cp -rv $ORIGEN/* $DESTINO/

echo "¡Backup completado con éxito!"
```
- !()[imagenes/a2.png]

Guardé los cambios con Ctrl + O y salí con Ctrl + X.

## 4. Asignación de permisos de ejecución
Para poder ejecutar el script, le di permisos:

```bash
chmod +x mibackups.sh
```
Y lo ejecuté:

```bash
./mibackups.sh
```
- !()[imagenes/a3.png]
El backup se realizó correctamente, pero apareció un problema importante.

## 5. Problema detectado: ineficiencia del comando cp
Aunque el script funcionaba, identifiqué un fallo de diseño:

- El comando funcian pero hay un error en la sintaxis que escribi en la terminal
- !()[imagenes/a4.png]
- El comando cp -rv copia todo cada vez.
- Si la carpeta pesa 10, 20 o 50 GB, el proceso se repetirá completo siempre.
- En entornos cloud (AWS, Azure, GCP), esto implica:
  - Gasto de tiempo: operaciones lentas e innecesarias.
  -   Gasto de dinero: tráfico de datos y operaciones de escritura que se cobran.


# 6. Solución para optimizar `memoria uso de rsync`:
Para evitar copiar archivos repetidos, sustituí la línea del cp por rsync, 
que solo sincroniza lo que ha cambiado.

La línea correcta es:

```bash
rsync -av --delete $ORIGEN/ $DESTINO/
```

- !()[imagenes/a5.png]
- Resultado
- !()[imagenes/a6.png]
- !()[imagenes/a7.png]
# ¿Qué hace este comando?
- `-a`: modo archivo (mantiene permisos, fechas, estructura).
- `-v`: modo verbose (muestra lo que está haciendo).
- `--delete`: elimina del destino los archivos que ya no existen en el origen.
- Solo copia archivos nuevos o modificados → eficiencia total.
- Este es el comportamiento esperado en un sistema de backup real.

## 7. Script final optimizado
El script queda así:

```bash
#!/bin/bash

ORIGEN="./proyectos"
DESTINO="./backups"

if [ ! -d "$DESTINO" ]; then
    mkdir -p "$DESTINO"
    echo "Carpeta de backup creada."
fi

rsync -av --delete $ORIGEN/ $DESTINO/

echo "Backup completado con rsync."

```
 ## 8. Conclusión
El ejercicio me permitió:
- Crear un script funcional desde cero.
- Detectar un problema de eficiencia típico en entornos profesionales.
- Sustituir una solución básica (cp) por una herramienta estándar en sistemas Linux (rsync).
- Comprender por qué en cloud es fundamental optimizar operaciones para evitar costes innecesarios.
