# 13. Bloqueando dispositivos de la red (dejándolos sin acceso a internet)

Veremos una herramienta llamada **EVIL LIMITER**, que nos va a servir para poder limitar el ancho de banda de un dispositivo que está en
nuestra red, a cómo hacer de que este dispositivo esté bloqueado completamente del acceso a Internet en la red.

Puede servir como broma, o en el caso de que tengamos a un cibercriminal en nuestra red conectandose al Internet, también podemos utilizar está
herramienta para limitarle el ancho de banda y hacer de que casi ni se pueda conectar a la red.

## Instalación

* Repositorio de GitHub: [EVIL LIMITER](https://github.com/bitbrute/evilimiter)

Nos da los pasos de instalación.

Abrimos una terminal y copiamos para clonar la herramienta:

```bash
git clone https://github.com/bitbrute/evilimiter.git
```

El próximo paso es dirigirnos al directorio:

```bash
cd evilimiter
```

El otro paso es:

```bash
sudo python3 setup.py install
```

Esto es para poder descargar herramientas, dependencias que requiere la herramienta para poder funcionar.

## Uso

Hacemos un:

```bash
ls
```

Veremos una carpeta llamada `bin/`. Si hacemos:

```bash
ls bin
```

Veremos un archivo llamado `evillimiter`. Hacemos un:

```bash
sudo python3 bin/evillimiter
```

Veremos el menú de la herramienta, nos dirá que ingresemos el comando `help` para ver las opciones que tenemos.

### Escanear dispositivos en la red

Vamos empezar escaneando dispositivos de red:

```bash
scan
```

Con este comando vamos a escanear dispositivos en la red Wi-Fi en la que estamos conectados. Nos dirá los hosts descubiertos.

Ahora, vamos a poner el comando:

```bash
hosts
```

Esto para ver los distintos dispositivos que están en nuestra red. Veremos una tabla así:

```plaintext
| ID | IP address | MAC address | Hostname | Status |
```

### Limitar ancho de banda

Ahora, tenmos nuestra máquina Windows virtualizando Kali Linux, buscamos la IP de nuestro dispositivo Windows.

Tenemos distintos IDs, para limitarle el ancho de banda a un dispositivo ponemos:

```bash
limit 4 200kbit --upload
limit 4 200kbit --download
```

* Usamos el ID que haga referencia a la dirección IP de nuestra computadora Windows

Esto, limitará el ancho de banda tanto de subida como de bajada. En nuestro caso, lo estamos limitando a 200kbit de carga/subida (`uload`) y de bajada (`dload`).

Si hacemos un [SPEEDTEST](https://www.speedtest.net/es), la **CARGA** nos mostrará 0.17 Mbps apróximadamente.

Si ejecutamos YouTube, nos va a estar cargando lento.

### Desbloquear dispositivos

Para desbloquear al dispositivo, hacemos:

```bash
free 4
```

Si ejecutamos SPEEDTEST nuevamente, tendremos los Mbps que teníamos antes de limitar el dispositivo.

### Bloquear dispositivos

Para bloquear la carga o descarga de un dispositivo, ponemos:

```bash
hosts
```

Escogemos el dispositivo, y ponemos:

```bash
block 4 --upload
```

En este caso, bloqueamos la carga. Si intentamos abrir YouTube, no nos cargará nada.
Si intentamos ejecutar SPEEDTEST, tampoco nos va a cargar nada.

Si queremos bloquearle la carga y descarga:

```bash
block 4 --upload
block 4 --download
```

Si intentamos abrir YouTube y SPEEDTEST, nos dirá que **No se puede acceder a este sitio web**.

Si ponemos:

```bash
free 4
```

Para sacarle las limitaciones que le pusimos anteriormente, el bloque de la red.

Ahora ya podremos acceder nuevamente a cualquier página web porque ya no tendremos más limitación.