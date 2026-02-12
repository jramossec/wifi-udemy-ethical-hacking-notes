# 10. Descubrir Hosts: Nmap

Veremos cómo escanear una red para encontrar dispositivos conectados a esa red.

Usaremos `nmap`:

```bash
nmap 192.168.0.1/24
```

Escaneará desde la IP privada `192.168.0.1` hasta `192.168.0.24`. Escaneará dispositivos o **hosts** entre esas 2 IPs en está **área local**.

La `192.168.0.1` es el **gateway**, **Access Point** o **Router**.

En el resultado del escaneo deberíamos ver:

```plaintext
PORT    STATE   SERVICE

# Luego, veremos algunos hosts en esta parte
# Ejemplos
Nmap scan report for 192.168.0.12
...

Nmap scan report for <hostname> (192.168.0.114)
```

No es una manera muy cómoda de escanear dispositivos en una red local, pero es una alternativa válida.