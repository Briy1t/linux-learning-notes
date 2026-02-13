# Ejercicio 3 — Regex avanzadas con ERE
En el archivo sistema.log hay líneas con distintos formatos, por ejemplo:

```text
2024-01-01 INFO Servicio iniciado
2024-01-01 WARN Conexión lenta
2024-01-01 ERROR Código 503
ID: A1234 Usuario: root
ID: B9876 Usuario: admin
```

Realiza las siguientes tareas:
- Extrae todas las líneas que contengan códigos alfanuméricos de 5 caracteres, usando [A-Za-z0-9]{5}.
- Muestra solo las líneas cuyo mensaje sea INFO, WARN o ERROR, usando grupos ( ) y alternancia |.
- Filtra las líneas que empiezan por una fecha válida usando:^[0-9]{4}-[0-9]{2}-[0-9]{2}
Obtén todas las líneas donde el usuario sea root o admin, usando:

```text
Usuario: (root|admin)
Muestra únicamente las líneas que no contienen números, usando grep -vE.
```
