# Ejercicio 1 — Análisis de logs con grep y regex
En una carpeta llamada logs/ tienes los siguientes archivos:
- app.log
- errores.log
- accesos.log
Cada archivo contiene líneas con distintos formatos, incluyendo:
- Fechas
- Códigos de error
- Mensajes de INFO, WARN y ERROR
- Direcciones IP
Realiza las siguientes tareas:
- Muestra únicamente las líneas que empiezan por ERROR en errores.log.
- Obtén todas las líneas que terminan en .txt dentro de app.log.
- Busca en accesos.log todas las líneas que contengan una dirección IP válida usando una regex con cuantificadores {1,3}.
- Filtra todas las líneas que contengan INFO o WARN, usando alternancia | con grep -E.
- Cuenta cuántas líneas contienen números de 3 dígitos consecutivos.
