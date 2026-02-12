# 20. Wordlists en Kali Linux

Vamos a ver las wordlists que tenemos en el sistema operativo Kali Linux.

## ¿Dónde están?

Están en el directorio `/user/share/wordlists`. Si nosotros vamos acá a este directorio:

```bash
cd /user/share/wordlists
ls
```

Tenemos wordlists para todo. Tenemos wordlist para lo que vendría siendo buscar directorios, buscar subdominios, para hacer ataques de fuerza
bruta a FTP, SSH, MySQl, con credenciales comunes.

Si vamos a `fern-wifi`, vamos a hacer un:

```bash
ls fern-wifi
```

Tenemos un `common.txt`, vamos a hacer un:

```bash
cat fern-wifi/common.txt
```

Y vamos a listar lo que vendría siendo el contenido y tenemos lo que vendría siendo posibles contraseñas de una red Wi-Fi.

Podemos también buscar en el directorio `seclists`:

```bash
cd seclists
ls
```

Tenemos para, por ejemplo, vamos ir a `Passwords`:

```bash
cd Passwords
ls
```

Tenemos de todo, tenemos una carpeta con credenciales default, vamos ir a:

```bash
ls Default-Credentials
```

Y acá tenemos credenciales comunes para FTP, para telnet, SSH, MySQL, está para Tomcat. Vamos a hacer un `ls` de vuelta y vamos a buscar acá
`WiFi-WPA`. Vamos a hacer un:

```bash
ls
ls WiFi-WPA
```

Y tenemos lo que vendría siendo wordlists, tenemos tres wordlits. Vamos a ver el contenido de esta:

```bash
cat WiFi-WPA/probable-v2-wpa-top447.txt
```

Acá tenemos posibles contraseñas. Son contraseñas muy comunes. Tenemos posibles contraseñas, contraseñas muy fácil de adivinar y las que son más
comunes.

Vamos a:

```bash
ls WiFi-WPA
```

Vamos a ver, tenemos está:

```bash
cat WiFi-WPA/probable-v2-wpa-top62.txt
ls
```

Tenemos posibles contraseñas. Nosotros lo que podemos hacer es poner todas esas contraseñas en un mismo archivo.

Podemos volcar todas las posibles contraseñas en un solo archivo y probarlas, y ver si algunas de ellas sirven para un ataque de fuerza
bruta.