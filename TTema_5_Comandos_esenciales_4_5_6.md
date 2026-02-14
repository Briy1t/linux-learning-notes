   4. Comandos de busqueda 
   5. Redirecciones y pipes / 5.1 Comandos de filtrado y ordenación
   6. Expresiones regulares (regex)


## 4 Comandos de búsqueda

- `grep` Busca una palabra o frase dentro de un archivo y muestra solo las líneas que coinciden.
`grep "PALABRA" archivo`

  - Esto es extremadamente útil para:
  - Encontrar fallos
  - Buscar usuarios
  - Buscar configuraciones
  - Filtrar logs
  - Analizar archivos grandes

1. Búsqueda sin distinguir mayúsculas/minúsculas
`grep -i "error" archivo`
Esto encuentra:ERROR, Error, error, eRrOr.
2. Mostrar números de línea
`grep -n "ERROR" archivo`
Te dice en qué línea aparece cada coincidencia.
3. Buscar en varios archivos a la vez
`grep "ERROR" *.log`
Busca en todos los archivos que terminen en .log.
4. Buscar dentro de carpetas completas (recursivo)
`grep -r "ERROR" /ruta/carpeta`
Busca en todos los archivos dentro de esa carpeta y subcarpetas.
5. Contar cuántas coincidencias hay
`grep -c "ERROR" archivo`
Te dice cuántas veces aparece la palabra.
6. Muestra todo menos las líneas con “ERROR”.
`grep -v "ERROR" sistema.log`

|Opción |Significado|
|:--|:--|
|-i |Ignorar mayúsculas/minúsculas|
|-n |Mostrar número de línea|
|-c |Contar coincidencias|
|-r |Búsqueda recursiva en carpetas|
|-v |Mostrar todo excepto lo que se busca|

## 5. Redirecciones y pipes

**Redirecciones**
- `> `sobrescribe un archivo con la salida de un comando.

- `>> `añade contenido al final sin borrar lo anterior.

- `< `usa un archivo como entrada para un comando.

**Pipes (|)**
Conectan comandos: la salida del primero pasa a ser la entrada del siguiente.

**Ejemplos típicos:**
- Filtrar: cat archivo | grep "texto"
- Contar resultados: grep "ERROR" log | wc -l
- Ordenar: grep "OK" log | sort
- Quitar duplicados: sort archivo | uniq

### 5.1 Comandos de filtrado y ordenación

1. `wc` :Cuenta líneas, palabras o caracteres.
`wc archivo`
- `wc -l` : olo líneas
- `wc -w `:solo palabras
- `wc -c` :solo caracteres
Muy útil con pipes: `grep "ERROR" log | wc -l`

2.`sort`:Ordena líneas.
orden alfabético

- `sort -n` orden numérico
- `sort -f` ignora mayúsculas
- `sort -k` 2 ordena por columna 2
Combinado con pipes: `cat usuarios | sort`

3. `uniq`:Elimina duplicados consecutivos.
limpia duplicados seguidos

- `uniq -d` muestra solo los duplicados
- `uniq -c` muestra cuántas veces aparece cada línea
Normalmente se usa con sort:`sort archivo | uniq`

## 6.Expresiones regulares (regex)

**Expresiones Regulares Extendidas (ERE)**: permiten utilizar operadores avanzados en grep sin necesidad de escapar metacaracteres.
Se activan mediante:

```bash
grep -E "patrón"
```

--- 

Con ERE se habilitan los operadores:

`| ` ` + ` ` ? ` ` { } `  `( )`

- Sin -E, algunos deben escaparse:

```bash
grep "ERROR\|WARNING"
```

Con ERE:

```bash
grep -E "ERROR|WARNING"
```

## 1. Diferencia entre | en shell y | en regex

**Shell (pipe)**
- `cmd1 | cmd2` → Transfiere la salida estándar de un comando a otro.
**Regex (alternancia)**
- `ERROR|WARNING` → Coincide con cualquiera de los dos patrones.

## 2. Metacaracteres básicos (ERE)

| Símbolo |	Función |	Ejemplo |
|:--|:--|:--|
|.	| Coincide con cualquier carácter	|a.b → acb, a-b|
|^ |	Inicio de línea |	^ERROR |
|$	| Final de línea |	txt$ |
| [] |	Conjunto o rango	| [0-9], [A-Za-z] |
| ` | `	| Alternancia  (OR)	| ``ERROR |	WARNING`` |

## 3. Cuantificadores

| Símbolo |	Descripción	| Ejemplo|
|:--|:--|:--|
|{n}| Exactamente n repeticiones	|[0-9]{3}|
|{n,m}|Entre n y m repeticiones | [A-Za-z]{2,5} |
| {n,} |	n o más repeticiones |	[0-9]{1,} |
| + |  	Una o más repeticiones | 	[0-9]+ | 
| * | 	Cero o más repeticiones | 	.* | 
| ? | 	Cero o una repetición | 	colou?r | 

## 4. Grupos
Los paréntesis permiten agrupar patrones y aplicar cuantificadores o alternancia a bloques completos.

Ejemplo:

```bash
grep -E "(ERROR|WARN|INFO)"
```

## 5. Guion y punto literal
Guion -
- Dentro de [] define rangos: [A-Z]
- Fuera de [] es literal: 123-ERROR

- Punto literal .
- Debe escaparse:

```bash
\.
```

## 6. Clases POSIX (válidas en ERE)
|Clase | Significado| 
|:--|:--| 
| [[:digit:]] | 	Dígitos (0–9) | 
| [[:alpha:]] | 	Letras | 
| [[:alnum:]]| Letras o números | 
| [[:space:]]| Espacios y tabulaciones| 

## nota 
- Metacaracter = símbolo con función especial en regex.
- Escapar = usar \ para que el símbolo pierda su función especial y se trate como literal.
- Sin -E → algunos operadores deben escaparse.
- Con -E → la mayoría de operadores avanzados funcionan sin escape.

## Ejercicios técnicos — Búsqueda, filtrado y regex (ERE)

### Ejercicio 1 — Análisis de logs con grep y regex
En una carpeta llamada logs/ tienes los siguientes archivos:
- inicio.log
- errores.log
- accesos.log
Cada archivo contiene líneas con distintos formatos, incluyendo:
- Fechas
- Códigos de error
- Mensajes de INFO, WARN y ERROR
- Direcciones IP
Realiza las siguientes tareas:
- Muestra únicamente las líneas que empiezan por ERROR en errores.log.
- Obtén todas las líneas que terminan en denegado dentro de inicio.log.
- Busca en accesos.log todas las líneas que contengan una dirección IP válida usando una regex con cuantificadores {1,3}.
- Filtra todas las líneas que contengan INFO o WARN, usando alternancia | con grep -E en inicio.log
- Cuenta cuántas líneas contienen números de 3 dígitos consecutivos en accesos.log

- [Solución Ejercicio 1](EjerAnálisis_de_logs_grep_y_egex.md)

### Ejercicio 2 — Pipes, filtrado y ordenación
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

- [Solución Ejercicio 2](Ejer2_Pipes_filtrado_ordenación.md)

### Ejercicio 3 — Regex avanzadas con ERE
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

- [Solución Ejercicio 3](Ejer3Regex_avanzadas_con_ERE.md)
