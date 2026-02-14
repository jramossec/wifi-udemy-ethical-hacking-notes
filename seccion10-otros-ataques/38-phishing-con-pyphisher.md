# 38. Phishing con PyPhisher

Vamos a ver esta herramienta de phishing que se llama **PyPhisher**.

## Instalación de PyPhisher

* Repositorio de GitHub: [PyPhisher](https://github.com/KasRoudra2/PyPhisher)

Vamos a proceder a instalarla. Acá nos da todo lo que son los pasos de instalación.

Primero, tenemos que instalar dependencias. Estas dependencias son aplicaciones que necesita esta aplicación para funcionar.

Estamos en un Kali Linux, así que vamos a copiar este comando:

```bash
sudo apt install git python3 php openssh-client -y
```

Vamos a pegar la selección, vamos a darle **Enter** y nos va a estar instalando todas estas dependencias.

Después tenemos que clonar el repositorio de GitHub. Lo que hacemos es que hacemos un `git clone`, vamos a copiar este comando:

```bash
git clone https://github.com/KasRoudra2/PyPhisher
```

O también:

```bash
git clone https://github.com/KasRoudra2/PyPhisher.git
```

Vamos a darle un **Enter** y acá se va a estar clonando la herramienta.

Ahora lo que vamos a hacer es que vamos a dirigirnos a la carpeta de la
herramienta de PyPhisher con:

```bash
cd PyPhisher
ls
```

Y acá tenemos estos archivos:
**files** (directorio), **LICENSE**, **pyphisher.py**, **README.md**

Lo que vamos a hacer es que vamos a instalar los requerimientos que necesite la herramienta para funcionar. Con el comando:

```bash
pip3 install -r files/requirements.txt
```

Lo que hacemos es copiar y pegar estos comandos que aparecen acá en esta instalación (GitHub). Y ahora vamos a esperar a que se realice la
instalación.

## Uso de PyPhiser

Una vez que tenemos instalados los requerimientos, ahora vamos a proceder a ejecutar lo que vendría siendo el PyPhisher, la herramienta.

Vamos a poner:

```bash
python3 pyphisher.py
```

Acá nos dice:

```plaintext
[?] Do you have loclx authtoken? [y/N/help]:
```

De una de las herramientas que utiliza el programa para funcionar.

* Vamos a ponerle que no, vamos a poner la `N`

Bueno, y ahora tenemos el menú de la herramienta. Vamos a seleccionar una de las opciones. Acá tenemos para hacer phishing en distintas páginas
web.

Tenemos desde Facebook hasta Instagram, hasta Gmail, PayPal, Netflix, Steam, montón de páginas web en la cual podemos hacer estos ataques de
phishing.

Vamos a seleccionar algunas de las opciones. En este caso, vamos a utilizar la página tradicional de Facebook para hacer este ataque de
phishing:

```plaintext
[?] Select one of the options > 1
```

* Vamos a poner la opción `1`

```plaintext
[?] Do you want OTP Page? [y/n] > n
```

* Vamos a darle que no `n`. En este caso **OTP** es un tipo de un factor de autenticación que utilizan las aplicaciones

Acá nos dice:

```plaintext
[?] Enter shadow url (for social media preview)[press enter to skip] :
```

* Vamos a poner un **Enter** para saltarnos este paso

```plaintext
[?] Enter redirection url [press enter to skip] :
```

* Vamos a darle de vuelta **Enter**

Y aquí nos va a estar generando lo que vendría siendo los links de phishing.
En este caso está inicializando un servidor PHP en el servidor local y ahora con las aplicaciones de **port forwarding**, lo que va a hacer es
que va a hacer que este servidor local se pueda acceder fuera de nuestra red local.

Acá tenemos tres links:

```plaintext
Ngrok

CloudFlared

LocalHostRun
```

Vamos a utilizar el link de `LocalHostRun`. Vamos a seleccionarlo y vamos a pegarlo (en un navegador).

Nosotros probemos cualquiera de estos tres links, pero el que funcionó en la clase y el que nos va a funcionar a nosotros es este link.

Acá nos dice:

```plaintext
[?] Wanna try custom link? [y or press enter to skip] :
```

* En este caso vamos a darle **Enter** para saltarnos este paso

Ahora lo que vamos a hacer es que vamos a ingresar el usuario y contraseña, vamos a simular que somos la víctima y que estamos en esta
página de Facebook.

Vamos a poner un nombre de usuario cualquiera, vamos a poner, un mail nos pide en este caso. Vamos a poner `mailfalso@gmail.com`.
No deja poner la arroba. Vamos a ponerle `mailfalsogmail.com`.

Y vamos a poner una contraseña cualquiera.

Vamos a darle en **Log In**. Y si volvemos a la aplicación, como podremos ver, tenemos la información que se capturó:

```plaintext
PyPhisher Data
[*] Facebook Username: mailfalsogmail.com
[*] Password: 1323213
```

Tenemos lo que vendría siendo el nombre de usuario. En este caso sería un mail, `mailfalsogmail.com` y la contraseña que nosotros pusimos
anteriormente.