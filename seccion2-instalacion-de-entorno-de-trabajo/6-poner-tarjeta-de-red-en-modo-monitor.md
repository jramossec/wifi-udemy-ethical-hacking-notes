# 6. Poner tarjeta de red en Modo Monitor

Vamos a ver a cómo conectar una tarjeta de red inalámbrica a Kali Linux.

## Verificar tarjeta de red inalámbrica (Windows)

Primero, debemos verificar que tengamos una tarjeta de red inalámbrica.

Para saber si tenemos una:

* Nos vamos a **Panel de control**
* Después, **Centro de redes y recursos compartidos**
* Después, **Cambiar configuración del adaptador**
* Identificamos la interfaz de red que tenemos y la red a la que estamos conectados, por el nombre **Wi-Fi** (no **Ethernet**)

No nos servirá **Ethernet**, ya que no podremos realizar ataques a redes inalámbricas.

## Configurando la tarjeta de red en VirtualBox

Nos vamos a VirtualBox:

* **Configuración** de la máquina virtual
* Nos vamos a **Red**:
  * **Conectado a:** Adaptador puente
  * **Nombre**: *Nuestra tarjeta de red*
* Nos vamos a **USB**, y marcamos **Habilitar controlador USB**:
  * Damos clic en **Agregar un nuevo filtro USB**
  * Seleccionamos nuestra tarjeta de red, la buscamos por la palabra **WLAN** y la marcamos para habilitar el uso de la tarjeta de red en la máquina virtual
* Le damos a **Aceptar**

## Iniciando la máquina virtual

Le damos a **Iniciar**.

Una vez iniciada la máquina virtual, se nos va a desconectar nuestro dispositivo principal, osea, no tendremos Internet. Pero la máquina
virtual sigue teniendo Internet.

En **Dispositivos**, verifiquemos que esté habilitada la tarjeta de red.

Entramos a la máquina, abrimos una termianl y ejecutamos:

```bash
ifconfig
```

Esto para ver las interfaces de red que tenemos en nuestro dispositivo.

Debemos ver:

* `eth0`: Por defecto
* `wlan0`: Nuestra tarjeta de red

Ahora, ejecutamos:

```bash
sudo airmon-ng start wlan0
```

Esto para poner nuestra tarjeta de red en **modo monitor**.

Ahora, si hacemos:

```bash
ping google.com
```

Si salió todo bien, nos debería salir:

```plaintext
ping: google.com: Fallo temporal en la resolución del nombre
```

Es decir, no podemos enviar paquetes con conexión a un cierto host, dispositivo, ip.

Y si hacameos:

```bash
ifconfig
```

Nos debería aparecer `wlan0mon`, que es la interfaz de red en modo monitor.

Ahora, podremos realizar una captura de red. Es bastante útil para el crackeo de redes WiFi.