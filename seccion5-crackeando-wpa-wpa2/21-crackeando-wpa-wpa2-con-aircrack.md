# 21. Crackeando WPA/WPA2 con aircrack

Vamos a ver cómo crackear una red Wi-Fi WPA2 con `aircrack-ng`.

## Uso

Ejecutamos:

```bash
sudo aircrack-ng -w diccionario2 -b <> Cap-01.cap
```

* `-w`: Para poner el diccionario, para realizar el ataque de fuerza bruta. Podemos descargar uno de Internet o usar el que nos convenga, en este caso usamos uno del proveedor de Internet, porque son muy fáciles de adivinar ya que es una secuencia que se repite en todas las redes Wi-Fi
* `-b`: Para poner el `BSSID` o la dirección MAC del Access Point, o cualquier Router
* `Cap-01.cap`: Archivo de captura. Los archivos de captura siempre son `.cap`

Esto va a crackear la red Wi-Fi WPA2, y esperamos a que el ataque de fuerza bruta termine.

Veremos la contraseña encontrada así:

```plaintext
...
KEY FOUND: [<contrasena-encontrada>]
...
```

Es la contraseña de la red Wi-Fi.