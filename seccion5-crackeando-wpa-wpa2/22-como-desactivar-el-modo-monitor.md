# 22. Como desactivar el modo monitor

Veremos cómo desactivar el modo monitor una vez que ya tenemos un ataque hecho, con la interfaz de red en modo monitor.

## Procedimiento

### Activar el modo monitor

Si tenemos la interfaz de red `wlan0`, la ponemos en modo monitor:

```bash
sudo airmon-ng start wlan0
```

Si hacemos:

```bash
ifconfig
```

La veremos como `wlan0mon`.

Si hacemos un:

```bash
ping google.com
```

No podemos enviar paquetes.

### Desactivar el modo monitor

Para desactivarlo y tener acceso a Internet:

```bash
sudo airmon-ng stop wlan0mon
```

>No necesariamente la interfaz se va a llamar `wlan0` y `wlan0mon`

Ya desactivamos el modo monitor.

Ahora, si queremos mandar paquetes a Google, y estamos conectados a una red Wi-Fi, podemos hacerlo:

```bash
ping google.com
```