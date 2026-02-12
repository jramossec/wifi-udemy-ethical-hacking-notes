# 31. Haciendo un Ataque Dos

Vamos a ver cómo hacer un ataque de denegación de servicio a un servidor.

En este caso, va a ser el servidor que tenemos en un área local que es el **Metasploitable2**.

## Metasploitable2

Vamos a:

```bash
ifconfig
```

Y vamos a sacar la IP. Lo que vamos a hacer es que vamos a colapsar este servidor para que no sea accesible.

Si vamos esta dirección IP (Metasploitable2) y la pegamos en el buscador, nos va a aparecer *Metasploitable2* y lo que vamos a hacer es
que vamos a tirar este servidor para que sea inaccesible.

Vamos a descargarnos **slowloris**.

## Descarga de slowloris

Repositorio de GitHub de `slowloris`: [GitHub slowloris](https://github.com/gkbrk/slowloris)

¿Cómo instalamos `slowloris`? Muy fácil, vamos a copiar estos comandos:

```bash
sudo pip3 install slowloris
```

Y se va a estar instalando `slowloris`.

Es una herramienta que nos permite hacer estos ataques, mandando paquetes **http**, haciendo peticiones **http**.

Las **peticiones HTTP** son las peticiones que realizamos cuando, por ejemplo, queremos solicitar un recurso en un servidor.

Realizamos una petición HTTP cuando queremos mandar un recurso a un servidor.

Existen muchos medios de petición, petición de tipo **POST**, petición de tipo **GET**, etc.

## Uso de slowloris

Una vez que ya lo tenemos instalado. Vamos a ver si funciona:

```bash
slowloris
```

Y lo que hacemos, es simplemente poner:

```bash
slowloris <host>
```

* `<host>`: Va a ser la dirección IP de la máquina Metasploitable2

Vamos a ir acá a la página de meta Metasploitable2 (dirección IP de la máquina):

```
http://<host>
```

Y si lo recargamos, funciona perfectamente.

Vamos a lanzar el ataque, damos enter al comando.

Acá se va a estar creando sockets, las peticiones para lanzarselo a el servidor.

Muy importante, es que si queremos hacer un ataque de denegación de servicio a una página web, que no es muy ético hacerlo y se nos recomienda
que no lo hagamos, **usemos una VPN**. Una VPN lo que hace es que nos cambia de dirección IP.

Bueno, vamos a recargar esta página de Metasploitable2. Aparentemente nos está recargando. Está como que no terminé de cargar.

Vamos a ver si accedemos a **Damn Vulnerable Web Application** (DVWA).

No podemos acceder. La página web no la está recargando, vamos a parar este ataque con `Ctrl+C`.

Y ahí si está cargando. Recién cuando pausamos el ataque, funciona.
Vamos a hacerlo de vuelta, la página recarga rapidísimo. Recarga sin ningún problema.

Vamos a lanzar el ataque de vuelta, vamos a recargar la página de Metasploitable2.
Y como veremos, no estaría cargando por el ataque que estamos haciendo.

Vamos a ir a "Damn Vulnerable Web Application", que es la página vulnerable. No nos deja.
**phpMyAdmin**, tampoco nos deja. **Mutillidae**, tampoco nos deja.
**WebDAV**, no nos deja. No nos deja acceder a ninguna página, no deja acceder a nada.

**¿Por qué?** Por esto mismo de que estamos haciendo un ataque de denegación de servicio. Estamos justamente mandando muchos paquetes,
estamos colapsando, estamos sobrecargando de los recursos computacionales del sistema atacado.

Estamos mandando muchas peticiones HTTP y el servidor lo que hace es que no las puede analizar, no puede realizar nada.

Nosotros, cuando queremos mandar una petición HTTP solicitando lo que vendría siendo acceder a estas páginas, no nos está dejando.

¿Por qué? Porque le estamos mandando, estamos llenando de peticiones HTTP y lo que hacemos es colapsar el servidor.

Bueno, esto es un ataque de denegación de servicio, muy simple, estamos haciéndolo en una área local, así que no hay ningún problema.

Nosotros, si queremos hacerlo, hagámoslo en una área local, en una computadora que tengamos acceso y en la que podamos realizar este tipo de
pruebas.

## Errores

### Instalación de slowloris

Para evitar usar `pipx` y crear un entorno virtual, se puede omitir está advertencia ejecutando:

```bash
sudo pip3 install slowloris --break-system-packages
```