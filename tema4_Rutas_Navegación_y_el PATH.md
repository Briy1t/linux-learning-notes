# Rutas, Navegación y el PATH
Este tema es fundamental porque todo en Linux son archivos y directorios, y necesitas saber moverte con precisión.


Lo vamos a dividir en tres partes:
1. Rutas absolutas y relativas
2. Comandos de navegación
3. La variable PATH (qué es y por qué importa)

## 1. Rutas absolutas vs. relativas

**Rutas absolutas**
Son rutas que empiezan desde la raíz /.
Ejemplos:
- /home/briyit
- /etc/ssh/sshd_config
- /var/log/syslog
- Siempre empiezan con /.
- Rutas relativas
- Son rutas que parten desde donde tú estás ahora.
**Ejemplos:**
Documents/
../ (subir un nivel)
./script.sh (archivo en el directorio actual)

## 2. Comandos de navegación
-`pwd`:Muestra dónde estás.
-`cd`:Moverse entre directorios.

**Ejemplos:**
`cd /etc`
`cd ..` (subir un nivel)
`cd ~ `(ir a tu home)
`cd -` (volver al directorio anterior)

- `ls`:Listar archivos.
Opciones útiles:
`ls -l `→ formato largo
`ls -a` → incluye archivos ocultos
`ls -lh `→ tamaños legibles


# 3. La variable PATH
Este punto es clave.
**PATH** es la lista de directorios donde Linux busca los comandos que ejecutas.
Cuando escribes:
Código
`ls`

Linux busca` ls` en los directorios del` PATH`.

Ejemplo típico de PATH:

Código
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin

Si un programa no está en el PATH, tienes que ejecutarlo con su ruta completa:
Código
/home/briyit/scripts/mi_script.sh

O añadirlo al PATH.


**Rutas absolutas →** empiezan con /
**Rutas relativas →** dependen de dónde estás
`pwd →` ver dónde estás
`cd → `moverte
`ls →` listar
`PATH →` dónde busca Linux los comandos

"./ significa “ejecútalo desde aquí”."




## SUBTEMA: Cómo Linux encuentra los comandos
Cuando tú escribes un comando en la terminal, por ejemplo:
Código:
`ls`

Linux hace un proceso muy específico para decidir qué ejecutar.
Ese proceso tiene un orden, y entenderlo te da control total del sistema.

1. **Linux ****NO**busca en todo el sistema
Esto es clave.
- **Linux **solo busca en los directorios que están en el PATH.
- Si el comando no está ahí, Linux no lo encuentra.
Por eso aparece:

`command not found`

2. Orden de búsqueda de comandos
Cuando escribes un comando, Linux sigue este orden:
1 ¿Es un comando interno del shell?
Ejemplo:
- cd
- echo
- pwd
Estos no son archivos, son funciones internas de bash.
2️ ¿Es una función o alias definido por el usuario?
Ejemplo:

`alias ll='ls -l'`

Si existe un alias, Linux lo usa antes que cualquier archivo.
3️ ¿Es un archivo ejecutable en el directorio actual?
`./script.sh`

**Linux NO**ejecuta automáticamente archivos del directorio actual por seguridad.
Por eso necesitas ./.

4️ Buscar en los directorios del PATH
Ejemplo típico de PATH:

`/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin`

Linux busca en ese orden.
Si encuentra el comando → lo ejecuta.
Si no → error.
# 3. ¿Por qué Linux no ejecuta cosas del directorio actual por defecto?
Por seguridad.

**Orden de búsqueda:**
1. Comandos internos del shell
2. Alias y funciones
3. ./archivo (directorio actual)
4. Directorios del PATH

# A tener en cuenta
PATH = lista de lugares donde Linux busca comandos
./ = ejecutar un archivo del directorio actual
which = ver dónde está un comando

- ¿Qué es el shebang? (#!/bin/bash)
Es la primera línea del script.
Ejemplo:

```text
#!/bin/bash
echo "Hola mundo"
```

El shebang le dice a Linux:
“Este script debe ejecutarse con este intérprete.”
Puede ser:
- #!/bin/bash
- #!/usr/bin/python3
- #!/bin/sh
- #!/usr/bin/env bash
Sin shebang, el script puede fallar o ejecutarse con el intérprete incorrecto.

¿Cómo convertir un script en un comando del sistema?
Crear el script
Añadir el shebang
Darle permisos de ejecución
Moverlo a un directorio del PATH:

`sudo mv script.sh /usr/local/bin/`


## SUBTEMA: Buenas prácticas de organización de archivos y scripts
Cuando trabajas en Linux, especialmente como administradora de sistemas, es fundamental mantener tus archivos, scripts y herramientas bien organizados. Esto evita errores, te ahorra tiempo y te permite trabajar como una profesional.

- **1. Dónde guardar tus scripts**
Hay tres lugares típicos, cada uno con un propósito claro:
    1️ `/usr/local/bin`
    Para scripts personales o de administración
      - Se ejecutan desde cualquier parte
      - No se sobrescriben con actualizaciones del sistema
      - Es el lugar recomendado para tus comandos personalizados
    Aquí guardarás tus futuros scripts profesionales.
    2️ `~/bin` (carpeta personal del usuario)
    - Solo para tu usuario
    - No afecta al sistema
    - Ideal para pruebas o scripts personales
    Si no existe, puedes crearla:
    `mkdir ~/bin`
    Y añadirla al PATH si no está.
    
    3️`/opt`
    Para aplicaciones completas instaladas manualmente
    No es para scripts pequeños
    Se usa más en entornos de servidores

**2. Nombres claros y consistentes**
Un buen script debe tener un nombre:
- corto
- claro
- sin espacios
- fácil de recordar
  
Ejemplos buenos:

backup_home
limpiar_logs
deploy_app

Ejemplos malos:
Código
script1.sh
cosas.sh
prueba_final.sh

**3. Siempre incluir un shebang**
Esto evita errores y asegura que el script se ejecute con el intérprete correcto.
Ejemplo:

`#!/bin/bash`

O si quieres máxima compatibilidad:

`#!/usr/bin/env bash`

**4. Dar permisos de ejecución**
Siempre:
`chmod +x script.sh`
Sin esto, el script no se ejecuta.

**5. Mantener tus scripts documentados**
Dentro del script, añade comentarios:
Código

```text

#!/bin/bash
# Este script limpia logs antiguos
```

Esto te ayuda a ti y a cualquier otra persona que lo use.

**6. No mezclar scripts con archivos del sistema
Nunca pongas scripts en:**
- /etc
- /usr/bin
- /var
- /root
Esos directorios son del sistema y no deben tocarse.

**7. Usar rutas absolutas dentro de scripts**
Ejemplo:

- /usr/bin/ls
- /bin/cp
- /usr/bin/grep

Esto evita errores cuando el PATH cambia.

- `/usr/local/bin →` scripts profesionales
- `~/bin →` scripts personales
-` shebang →` obligatorio
- `chmod +x →` permisos de ejecución
- nombres claros → profesionalidad
- comentarios → mantenimiento
- rutas absolutas → estabilidad



