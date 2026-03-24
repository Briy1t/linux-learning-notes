# FIND — BÚSQUEDA AVANZADA EN LINUX
 
# 1. ¿Qué es find?
`find` = sirve para buscar archivos, carpetas y dispositivos dentro del sistema.
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

- “find /path es la ruta donde estan los archivos para ser encontrados .”
- La sintaxis es:
  
```bash
find /ruta -type tipo -name "patrón"
```
---

**Ejemplos de rutas**:

- / → raíz
- . → carpeta actual
- /home/briyit/ → ruta específica

### 3. Tipos de archivo (-type)
De tu documento: “f – Archivo regular… d – Carpeta… l – Enlace simbólico… c – Dispositivos de caracteres… b – Dispositivos de bloque.”
- Los más usados:

| Tipo | Significado |
|:--|:--|
|type f | archivo normal |
|type d | carpeta |
|type l |enlace simbólico |
|type c | dispositivo de caracteres |
|type b |dispositivo de bloque |

---
**Ejemplo:**

```bahs
find . -type d
```
- Busca solo carpetas.

### 4. Buscar por nombre (-name)
De tu documento:
`“find . -type f -name "style*"”`
- **Ejemplos:**
- Archivos que empiezan por “style”
```bash
find . -type f -name "style*"
```
- Archivos .html
```bash
find . -type f -name "*.html"
```
- Archivos ocultos
```bash
find . -type f -name ".*"
```
### 5. Buscar por tamaño (-size)
De tu documento:
- “find / -size +250M”
- Unidades:
- G → gigas
- M → megas
- K → kilobytes
- c → bytes
- **Ejemplos:**
Archivos mayores de 100 MB
```bash
find / -type f -size +100M
```
- Archivos menores de 10 KB
```bash
find . -type f -size -10K
```

### 6. Buscar por fecha (-mtime)
De tu documento:
- “-mtime +10 significa que estás buscando un archivo que se modificó hace 10 días.”
**Ejemplos:**
- Archivos modificados hace más de 10 días
```bash
find . -mtime +10
```
- Archivos modificados hace menos de 3 días
```bash
find . -mtime -3
```
- Archivos modificados exactamente hace 1 día
```bash
find . -mtime 1
```
### 7. Buscar carpetas
De tu documento:
- “find . -type d”
- **Ejemplo:**
``` bash
find /home -type d
```
### 8. Buscar dispositivos (avanzado)
De tu documento:
- “find / -type c”
- “find / -type b”
- **Ejemplos:**
- Dispositivos de caracteres
```bash
find /dev -type c
```
- Dispositivos de bloque
```bash
find /dev -type b

### Ejercicio

- [Ejercicio comando find](Ejer_find.md)


```

### 9. EJERCICIO 
