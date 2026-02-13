# Ejercicio 2 — Pipes, filtrado y ordenación
En un archivo llamado usuarios.txt tienes una lista desordenada de usuarios, algunos repetidos, con el siguiente formato:

- nombre apellido edad
Ejemplo:
```text
ana lopez 22
carlos ruiz 31
ana lopez 22
maria torres 19
```

Realiza las siguientes tareas usando pipes y comandos de filtrado:
- Ordena el archivo por edad (columna 3) de forma numérica.
- Muestra solo los usuarios únicos, sin duplicados.
- Cuenta cuántos usuarios tienen edad entre 20 y 29, usando una regex con rangos [2][0-9].
- Muestra únicamente los usuarios cuyo apellido empieza por vocal, usando grep -E.
- Genera una lista ordenada alfabéticamente de nombres (columna 1), sin repetir.
