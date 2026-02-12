# 14. Cambiando dirección MAC

Veremos como cambiar la dirección MAC de un dispositivo de red.

## Utilidad deambiar la dirección MAC de la tarjeta de red

La dirección MAC es un número que identifica a una tarjeta de red, cambiarla nos sirve para tener un poco más de privacidad a la hora de
acceder a Internet. Ya que al cambiar ese número, ya no e vincula esa dirección MAC con nosotros.

Esto sirve por ejemplo, *se pone nuestra dirección MAC en una lista negra*, en la cual si el servidor o un dispositivo detecta está dirección
MAC en la red, la bloquea del acceso.

Cambiar la dirección MAC de la tarjeta de red a una direccción que esté permitida en la red y que esté en la *lista blanca*, nos permitirá
acceder a la red.

## MAC Changer

Para lograr esto, lo haremos con un programa llamado **MAC Changer** que por defecto está instalado en Kali Linux, sino, hacemos:

```bash
sudo apt-get install macchanger
```

### Uso

Hacemos:

```bash
sudo macchanger --help
```

Para ver las distintas opciones que tenemos.

El uso es:

```plaintext
Usage: macchanger [options] device
```

* `device`: Es el dispositivo que estamos utilizando.

Hacemos un:

```bash
ifconfig
```

Para saber el dispositivo que estamos utilizando. Puede ser `eth0`, `wlan0`, lo que sea. Pero guardemos la dirección MAC:

```plaintext
eth0: ...
        ether <direccion-MAC>
```

Para que luego comprobemos que si se cambia la dirección MAC.

Este es valor por defecto, de fábrica de nuestro dispositivo de red.

Ahora, lo cambiamos con:

```bash
sudo macchanger -r
```

* `-r`: Nos sirve para poner una dirección MAC random
* `-m`: Nos sirve para poner una dirección MAC en específico

Ejemplo con `-m`:

```bash
sudo macchanger -m 10:20:e7:56:dh:tb eth0
```

* `eth0`: Nuestra interfaz de red

Nos mostrará un mensaje de confirmación:

```plaintext
Current MAC:    <direccion-MAC>
Permanent MAC:  <direccion-MAC>
New MAC:        10:20:e7:56:0d:00 (unknown)
```

Si hacemos un:

```bash
ifconfig
```

Veremos que cambió la dirección MAC del dispositivo. En la red tenemos está dirección MAC:

```plaintext
eth0: ...
        ether 10:20:e7:56:0d:00
```

Ya no tenemos la anterior.

Si queremos volver a poner la anterior, copiamos la `Permanent MAC`, que vendría a ser una dirección MAC que viene por defecto en el dispositivo:

```bash
sudo macchanger -m <direccion-MAC> eth0
```

Para poner una dirección MAC random:

```bash
sudo macchanger -r eth0
```

Si hacemos un:

```bash
ifconfig
```

Veremos que tenemos está dirección MAC para el dispositivo de red:

```plaintext
eth0: ...
        ether <direccion-MAC-random>
```

## Resumen

Cuando vamos a hacer un ataque en red, algún ataque de **cracking de contraseñas a redes Wi-Fi** o cualquier ataque en red, sirve mucho
cambiar nuestra dirección MAC para conservar nuestra privacidad y que no se asocie la dirección MAC que tenemos a nuestra computadora.