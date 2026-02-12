# 27. Protocolo ARP

Vamos a ver qué es el **protocolo ARP**, que es el protocolo de resolución de direcciones.

## Protocolo ARP

Es un protocolo de comunicaciones de la capa de enlace de datos en el modelo OSI y es el responsable de encontrar la *dirección MAC* que
corresponde a una *dirección IP*.

Una **dirección MAC** pertenece a la tarjeta de red, que es una dirección que pertenece a la tarjeta de red y corresponde a una dirección IP.

Por eso, lo que se hace es que se manda un paquete ARP a la dirección, al **broadcast**. Contiene la dirección IP con la que se pregunta y se espera
a que esa máquina u otra responda con un paquete **arp reply**, osea, una respuesta con la dirección Ethernet, con la dirección MAC que le corresponde.

En la próxima clase, vamos a ver cómo envenenar este protocolo. Vamos a ver qué es el **ARP Poisoning**.