# Interfaz en Linux 

Es el (GUI) es la parte visual del sistema: ventanas,iconos,menùs, paneles. aplicaciones, etc.
Es lo que no ves en la terminal 

---
**Linux** puede tener diferentes escritorios, según la distribución:
- GNOME (Ubuntu, Fedora)
- KDE Plasma (Kubuntu)
- XFCE (Xubuntu)
- MATE
- Cinnamon (Linux Mint)

## 1. Elementos
1. **Escritorio**:Es el fondo donde puedes
- poner archivos
- poner accesos directos
- cambiar el fondo de pantalla
  1.1 **Barra superior o inferior**:Depende del escritorio, pero normalmente incluye
    - hora
    - red
    - volumen
    - batería
    - menú de aplicaciones
2**Menú de aplicaciones**:Es como el “Inicio” de Windows.Desde aquí abres
- navegador
- terminal
- archivos
- Configuraciones
- programas instalados
3. **Ventanas**: Cada aplicación se abre en una ventana con:
 - botón cerrar
 - minimizar
 - maximizar
4. **Explorador de archivos**Se llama:
- Nautilus (`GNOME`)
- Dolphin (`KDE`)
- Thunar (`XFCE`)
---
**Sirve para:**
- navegar carpetas
- copiar/mover archivos
- crear carpetas
- eliminar archivos

## Puedes
1. **Navegar por carpetas** : Como en Windows, pero con rutas Linux:
  - /home
  - /etc
  - /usr
  - /var
- **Abrir aplicaciones**:Navegador, editor de texto, terminal, etc.
- **Configurar el sistema** :Red, sonido, pantalla, usuarios, idioma…
  
2.**Instalar programas**: Según la distribución:
- `Ubuntu` → Software Center
- `Fedora` → Discover
- `Linux Mint` → Gestor de software

3.**Usar la terminal**:La GUI siempre tiene un acceso a la terminal.

## Diferencias entre GUI y Terminal
|GUI | Terminal |
|:--|:--|
|Fácil, visual |Precisa, rápida |
|Ideal para principiantes | Ideal para administradores |
|Más lenta |Más poderosa |
|No siempre muestra todo | Control total |


---

La interfaz gráfica de **Linux** se parece mucho a Windows en lo visual:
- escritorio
- iconos
- ventanas
- barra de tareas
- menú de aplicaciones
---
El menú de aplicaciones es como el botón “Inicio” de Windows.En Linux puede llamarse:
- “Activities” (GNOME)
- “Menu” (XFCE)
- “Kickoff” (KDE)
- “Menu de Linux Mint” (Cinnamon)
Pero siempre sirve para lo mismo:

--- 
| GUI | Terminal |
|:--|:--|
|Visual |Texto | 
| Fácil | Precisa |
| Lenta | Rápida |
| Para usuarios | Para administradores |

---

## 2. CONFIGURACIÓN DEL SISTEMA DESDE LA INTERFAZ GRÁFICA
En **Linux**, la configuración gráfica se encuentra en:
- Configuración del sistema 
- Settings  
- Ajustes  
- System Settings
    Cuando lo abres, verás categorías como:
    - Red
    - Pantalla
    - Sonido
    - Usuarios
    - Energía
    - Actualizaciones
    - Bluetooth
    - Ratón y teclado
    - Es igual que en Windows, solo que organizado de otra forma.
      
### 2. Configuración de red 
Aquí puedes:
- conectarte al WiFi
- configurar red cableada
- ver la IP
- activar/desactivar redes
- cambiar DNS (muy útil)


### 3. Configuración de usuarios
Desde la interfaz gráfica puedes:
- crear usuarios
- cambiar contraseña
- cambiar foto de perfil
- activar/desactivar cuentas
- cambiar tipo de usuario (normal / administrador)

### 4. Configuración de pantalla
Aquí puedes:
- cambiar resolución
- cambiar brillo
- configurar varios monitores
- cambiar orientación
- cambiar fondo de pantalla
  
### 5. Configuración de sonido
Puedes:
- cambiar volumen
- elegir salida (altavoces, auriculares)
- elegir entrada (micrófono)
- probar dispositivos
  
### 6. Configuración de actualizaciones
En Ubuntu, por ejemplo:
- Software & Updates
- Actualizaciones automáticas
- Repositorios :desde aquí puedes:
- activar actualizaciones automáticas
- elegir servidores de descarga
- instalar drivers
### 7. Configuración de energía
Puedes:
- suspender
- hibernar
- apagar pantalla
- configurar batería
### 8. ¿Por qué es importante aprender esto si tú usarás terminal?
Porque Linux+ exige que conozcas ambos mundos:
- GUI
- Terminal
- Fácil
- Precisa
- Visual
- Rápida
- Para usuarios
- Para administradores
---
necesitas saber:
Dónde están las cosas en la GUI
cómo se hace lo mismo en terminal

---
¿Qué **NO** es la interfaz gráfica?
- La terminal
- La pantalla negra con comandos
- El modo texto
- El shell
- Eso es CLI (Command Line Interface).

---
Para identificar tu interfaz gráfica (entorno de escritorio) en Linux, utiliza el comando `echo $XDG_CURRENT_DESKTOP`

- Abre una terminal (Ctrl+Alt+T) y escribe:
```bash
echo $XDG_CURRENT_DESKTOP
```
imagen

##
