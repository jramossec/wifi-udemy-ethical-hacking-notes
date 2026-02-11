# 4. Instalación de metasploitable2

**Metasploitable2**, es una máquina vulnerable la cual vamos a utilizar para hacer ataques web, todo tipo de ataques que los vamos a ver a lo
largo del curso.

## Instalación de Metasploitable

* Buscamos en Google **metasploitable 2**
* Vamos al resultado de la página de [SourceForge](https://sourceforge.net/projects/metasploitable/files/Metasploitable2/)
* Le damos a **Download Latest Version** y se va a estar descargando el archivo `.zip` que contiene la máquina virtual de Metasploitable

## Configuración en VirtualBox

### Creación y configuración de la máquina virtual

* Una vez descargado, lo extraemos.
* Nos vamos a VirtualBox, cremos una nueva máquina virtual:
  * Nombre: **metasploitable2**
  * Tipo: **Linux**
  * Subtype: **Linux 2.6**
* Sección de **Disco duro**, seleccionamos **Usar un archivo de disco duro virtual existente**
* Nos vamos al icono de carpeta, le damos clic en **Añadir**
* Nos vamos a la carpeta en la cual extraimos el Metasploitable2
* Seleccionamos el **Virtual Machine Disk** Metasploitable
* Le damos en **Abrir**
* Le damos en **Seleccionar**
* Le damos en **Terminar**

Una vez que tengamos la máquina virtual creada:

* Vamos a darle en **Configuración**
* En **Red**
* Seleccionamos **Adaptador puente**
* Elegimos nuestra tarjeta de red
* Le damos en **Aceptar**

## Corriendo máquina virtual

* Le damos en **Iniciar**
* Nos dirá por pantalla cuál es el usuario y contraseña:
  * User: **msfadmin**
  * Password: **msfadmin**

Este sistema Linux Metasploitable2 se maneja vía consola, vía comandos, no tiene interfaz gráfica.

Si hacemos un:

```bash
ifconfig
```

Nos va a dar la dirección IP de esta máquina Linux vulnerable. Con este dato de la dirección IP, luego podemos hacer ataques.

Y si ingresamos la dirección IP de la máquina Metasploitable2 en el navegador vamos a tener muchas páginas web vulnerables, las cuales
podemos atacar y poder realizar muchos ataques web.