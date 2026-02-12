# 15. Empezando el Ataque

Vamos a empezar a hackear una red **WPA2**, que es el cifrado que tiene que ver para todo el tema redes más utilizado en redes domésticas.

**WEP** ya no se utiliza, si bien es fácil de hackear este protocolo, no se utiliza mucho y no vale la pena. Es más importante aprender a cómo
crackear WPA2 y WPA, que es lo mismo pero WPA2 es más seguro.

## Para empezar el ataque

Hacemos un:

```bash
ifconfig
```

Para ver si tenemos una tarjeta de red wireless `wlan0`. Hacemos un:

```bash
iwconfig
```

Nos debe aparecer la tarjeta de red `wlan0`. Y vamos a ponerla en modo monitor.

Antes de hacer todo esto, ponemos:

```bash
sudo airmon-ng check kill
```

Para matar procesos que estén interfiriendo con la tarjeta de red. Suele ser `wpa_supplicant` el proceso que siempre está estorbando.

Ahora ponemos la tarjeta en modo monitor:

```bash
sudo airmon-ng start wlan0
```

Ahora hacemos:

```bash
ifconfig
```

Nos debe aparecer `wlan0mon`. Para comprobar que estamos en modo monitor:

```bash
ping google.com
```

No debemos poder mandar paquetes, porque la tarjeta de red en modo monitor, no podemos realizar ningún tipo de conexión.

El **modo monitor** sirve para capturar todo el tráfico que está en la red.

Ahora, hacemos:

```bash
sudo airdump-ng wlan0mon
```

Aquí va a estar mapeando todas las redes Wi-Fi que encuentra, y vamos a elegir la víctima que queremos hackear. Elegimos la red de nuestra casa.

Una vez que tenemos el objetivo elegido, vamos a realizar una captura de **Handshake**.