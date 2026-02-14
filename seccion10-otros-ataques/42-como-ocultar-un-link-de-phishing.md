# 42. Como ocultar un link de phishing

Vamos a ver a cómo camuflar un link de phishing con la herramienta **MaskPhish**.

## Clonando la herramienta

Copiamos el link:

* Repositorio de GitHub: [MaskPhish](https://github.com/jaykali/maskphish)

Hacemos:

```bash
git clone https://github.com/jaykali/maskphish.git
```

## Uso

Nos vamos al directorio:

```bash
cd maskphish
ls
```

Hacemos:

```bash
sudo bash maskphish.sh
```

Nos pide que pongamos una URL de link de phishing, hacemos una y la pegamos:

```plaintext
### Phishing URL ###
Paste Phishing URL here (with http or https): https://<content>.ngrok.io
```

Ahora, nos pedirá la URL en la cual queremos enmascarar el link de phishing. Vamos a poner la URL de Instagram:

```plaintext
### Masking Domain ###
Domain to mask the Phishing URL (with http or https), ex: https://google.com, http://anything.org) :
=> https://instagram.com
```

Después, nos pide palabras de ingeniería social En este caso vamos a poner:

* `support`: Porque vamos a hacer pasar nuestra página de phishing por un soporte de Instagram

```plaintext
Type social engineering words:(like free-money, best-pubg-tricks)
Don't use space just use '-' between social engineering words
=> support
```

Y ya tenemos el link de phishing generado:

```plaintext
Generating MaskPhish Link...

Here is the MaskPhish URL: https://instagram.com-support@is.gd/tjPTaC
```

Copiamos y pegamos el link en el navegador. Nos dirá que por motivos de seguridad no accedamos al link porque puede ser peligroso.
En Chrome no pide esto pero Firefox sí. Le damos a **Yes**.

Ponemos un usuario y contraseña aleatorios y le damos a **Log in**.

Y si vamos a la terminal donde tenemos el servidor de phishing, vemos que se ha recibido la información:

```plaintext
[ CREDENCIALES ENCONTRADAS ]:
[EMAIL]: usuario123 [PASS]: 1234
========================================================
========================================================

[ INFORMACION DE LA VICTIMA ENCONTRADA ]:
...
```

En información de la víctima, vemos la direción IP, la ciudad de la provincia, etc.

Esta herramienta nos sirve para enmascarar un link para que sea un poco más verídico, que no sea el típico `ngrok`, que si vamos a hacer un
ataque de phishing, no es lo más creible para la víctima.

## **Herramienta de phising usada para generar el link**

* Repositorio de GitHub [YPhish](https://github.com/thiagoaraujosec/YPhish)