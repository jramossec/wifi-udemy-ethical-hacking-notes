# 29. Ataque MITM/ARP Poissoning

Vamos a ver cómo hacer este ataque, un ataque **Man in the Middle** o un ataque **ARP Poisoning**.

## Ataque Man in the Middle (MitM) - ARP Poisoning

Un ataque **Man in the Middle** lo que permite es que un atacante se ponga entre medio de una conversación, entre un cliente y un servidor.

Lo que nos permite es obtener datos de esa conversación, datos como por ejemplo, contraseñas y datos que se están circulando en la red.

## Ettercap

Vamos a buscar **Ettercap**. Es una herramienta para hacer ataques **Man in the Middle**.

Vamos a poner la contraseña para autenticarnos.

## Uso de Ettercap

Vamos a poner la interface de red. En nuestro caso, es *Ethernet cero* (`eth0`).

Vamos a darle Enter :white_check_mark:.

Vamos a darle **Hosts List**.

Acá nos está buscando, vamos a ponerle acá en las tres rayitas y vamos a poner **Hosts** y vamos a escanear por hosts (**Scan for hosts**), vamos a
escanear por direcciones IP que encuentre.

Acá encontró bastantes. Vamos a, lo que vendría siendo, buscar la dirección IP de la máquina víctima.

En nuesto caso, vamos a utilizar:

```bash
netdiscover
```

Por `netdiscover`, vamos a buscar hosts en los cuales vamos a realizar lo que vendría siendo estos ataques.

Una vez encontramos la dirección IP de la víctima, vamos a agregar como *Target 1* (**Add to Target 1**) y el gateway, o el router, vamos a
ponerle como *Target 2* (**Add to Target 2**).

Vamos a ir donde dice *Man In The Middle menu* (**MITM menu**) y vamos a poner **ARP poisoning...**. Vamos a ponerle **OK**.

Y se va a estar haciendo lo que vendría siendo el ataque de ARP, envenenamiento del protocolo ARP.

Ahora si la victima va a una página **http** e ingresa credenciales, nos van a llegar a nosotros.

Vamos a ir a la página del router, la página en la cual se ingresa al menú del router. Puede ser:

```plaintext
http://192.168.0.1/
http://192.168.1.1/
```

Vamos a poner el usuario y contraseña: "admin", por poner una contraseña "admin". Vamos a ponerle **Apply**.

Bueno, vamos a ver ahora en la máquina del atacante. Y aparece que se encontró un usuario y contraseña:

```plaintext
CONTENT: ...loginUsername=admin&loginPassword=admin...
```

Acá es como logramos con lo que vendría siendo capturar contraseñas por medio de este ataque.

Este ataque, también se puede hacer en páginas https, pero eso es con **SSL Strip** que no lo vamos a mostrar en esta clase porque es algo muy
simple.

Pero bueno, podemos capturar credenciales `admin` y `admin`, que vendría a ser el usuario y contraseña. Y esto vendría siendo el ataque.