# 43. Acortar Links de phishing

Vamos a ver cómo camuflar links de phishing por medio de un acortador de links, para que al mandar a nuestra víctima que no aparezca el link de ngrok:

```plaintext
https://<content>.ngrok.io
```

Porque es muy sospechoso y no dan ganas de entrar a ese tipo de links.

## bitly

Vamos a utilizar una herramienta llamada [bitly](https://bitly.com/), que sirve para acortar links.

## Uso

Vamos a la página de bitly, pegamos el link en *Shorten your link* y le damos a **Shorten**.

Copiamos el link acortado `https://bit.ly/3qtAFQY` (ejemplo), y si accedemos a este link, nos redirige a la página de Instagram.

Ponemos un usuario y una contraseña cualquiera, le damos a **Log in** y nos dará las credenciales y más información de la víctima que encontró:

```plaintext
[ CREDENCIALES ENCONTRADAS ]:
[EMAIL]: user1234 [PASS]: 1234
========================================================
========================================================

[ INFORMACION DE LA VICTIMA ENCONTRADA ]:
...
```

Este es otro método para camuflar links de phishing, también podemos utilizar [tinyurl](https://tinyurl.com/).

## **Herramienta de phising usada para generar el link**

* Repositorio de GitHub [YPhish](https://github.com/thiagoaraujosec/YPhish)