# 32. Ataque Dos con golang-httpflood

Vamos a ver a cómo realizar un ataque de denegación de servicio a una máquina Metasploitable2, en un entorno local, y vamos a dejarla fuera de
conexión.

Vamos a utilizar la herramienta **Golang-httpflood**, que es para realizar peticiones al HTTP:

* Repositorio de GitHub: [Golang-httpflood](https://github.com/Leeon123/golang-httpflood)

En este caso, a este servidor de Metasploitable2.

## Instalación

Copiamos:

```bash
git clone https://github.com/Leeon123/golang-httpflood.git
```

Hacemos:

```bash
cd golang-httpflood
```

## Golang

Antes, tenemos que tener instalado **Golang** (Go), que es un lenguaje de programación que utiliza está herramienta. Lo instalamos con:

```bash
sudo apt install golang-go
```

Hacemos un:

```bash
ls
```

Debemos construir el archivo `httpflood.go`. Para eso, hacemos:

```bash
go build httpflood.go
```

Tendremos el archivo `httpflood`, vamos a ejecutarlo.

## Uso

Ponemos:

```bash
./httpflood http://<ip-host> 100000 get 60 nil
```

* `http://<ip-host>`: URL con la IP de la máquina víctima
* `100000`: Threads de ejecución. Cuantos más threads/hilos de ejecución pongamos, cuantos más paquetes enviemos, mucho mejor y más rápido se va a tumbar el servidor
* `get`: Tipo de petición que queremos hacer. En este caso, hacemos una petición GET, es decir, solicitar un archivo/recurso al servidor
* `60`: Segundos que va a durar el ataque. En este caso, queremos que dure 60 segundos
* `nil`: Header, pero con este valor podemos no especificar un Header de la petición

Mientras se ejecuta, se van a cargar los hilos de ejecución. Entre más pongamos, más se va a tardar en cargar.
Nos pedirá **Enter** para continuar, y nos dirá que *el spam de paquetes va a terminar en 60 segundos*.

Si intentamos recargar el servidor, va a tardar en cargar y en algún momento se va a tumbar el servidor.

Nos vamos a la máquina Metasploitable2, y hacemos:

```bash
ifconfig
```

Y si nos fijamos en los `RX packets` y `TX packets`, veremos que el número va subiendo. Eso vendrían siendo las peticiones que va recibiendo
el servidor.

Si vemos el panel de ejecución de la herramienta, nos dirá que la conexión con el servidor se cayó.

Si volvemos a recargar la página, nos dirá que ya no se puede conectar al servidor.

Básicamente tumbamos el servidor con este ataque de denegación de servicio, con este spameo de peticiones HTTP al servidor. En este caso,
mandamos 100,000 peticiones, 100,000 hilos por segundo, 100,000 peticiones por segundo.