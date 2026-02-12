# 19. Descargar Wordlists

Vamos a ver a cómo descargar wordlists de GitHub para nuestros ataques de fuerza bruta.

Nosotro queremos hacer un ataque de fuerza bruta a un servicio FTP, un servicio SSH, hacer un ataque de contraseñas, necesitamos descargar una
wordlist.

Lo mismo para hacer un ataque a redes Wi-Fi, a servicios, a redes sociales.

En GitHub hay bastantes repositorios con wordlist.

Buscamos **wordlist github** en Google.

## Wordlists en Kali Linux

Ya de por si, en Kali Linux si buscamos cosas con:

```bash
locate wordlist
```

Vamos a localizar las wordlists que hay en el sistema.

De la selección vamos a hacer:

```bash
cat /usr/share/wordlists/rockyou.txt
```

Y veremos que hay un montón de posibles contraseñas.

Pero también es bueno descargar wordlists de Internet que quizás son un poco más completas.

## Descargando wordlists de GitHub

Vamos a algún repositorio:

* [Probable-Wordlists](https://github.com/berzerk0/Probable-Wordlists)

Y hacemos:

```bash
git clone https://github.com/berzerk0/Probable-Wordlists.git
```

Hacemos a:

```bash
cd Probable-Wordlists
ls
```

Y tenemos estos archivos:

```plaintext
Analysis-files Changelog.md Contributing.md Dictionary-Style Downloads.md License.txt ProbableWordlistLogo.png README.md Real-Passwords
```

Vamos a la carpeta:

```bash
cd Real-Passwords
ls
```

Tenemos un diccionario `Top1575-probable-v2.txt`, miramos el contenido del archivo:

```bash
cat Top1575-probable-v2.txt
```

Podemos descargar wordlists de todo tipo únicamente buscando en GitHub y descargando los repositorios.

* Otro repositorio: [wordlist](https://github.com/jeanphorn/wordlist)