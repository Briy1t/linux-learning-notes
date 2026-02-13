Ejercicio: Lectura y exploración de archivos en Linux
 Imagina que estás trabajando en un servidor y tienes los siguientes archivos dentro del directorio /var/logs/app/:
  - inicio.log (archivo pequeño con 15 líneas)
  - errores.log (archivo muy grande que crece constantemente)
  - config.txt (archivo de configuración con 50 líneas)
  - registro_hoy.log (archivo que se actualiza en tiempo real)
Realiza las siguientes tareas usando únicamente los comandos:
  cat, head, tail, less, tail -f.

Tareas:
  - Comprueba rápidamente si el archivo inicio.log contiene la palabra “OK” en sus primeras líneas.
  - Visualiza solo las primeras 5 líneas del archivo config.txt.
  - Abre el archivo config.txt para navegarlo página por página y buscar dentro la palabra “timeout”.
  - Revisa únicamente las últimas 10 líneas del archivo errores.log sin mostrarlo completo.
  - Monitorea en tiempo real el archivo registro_hoy.log para ver si aparecen nuevas entradas.
  - Muestra el contenido completo de inicio.log de una sola vez, ya que es un archivo pequeño.
  - Consulta las últimas 20 líneas de errores.log sin abrirlo en un visor.
