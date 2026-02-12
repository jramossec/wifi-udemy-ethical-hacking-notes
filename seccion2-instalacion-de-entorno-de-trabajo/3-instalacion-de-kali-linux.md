# 3. Instalación de Kali Linux

**Kali Linux** es un sistema operativo basado en Linux que cuenta con un montón de herramientas de hacking ético y ciberseguridad.

Link de descarga de la imagen ISO de [Kali Linux](https://www.kali.org/get-kali/#kali-installer-images)

## Configuración de Kali Linux en VirtualBox

Una vez descargada, vamos a ir a VirtualBox y vamos a darle clic en **Nueva**, para crear una nueva máquina virtual, elegimos la imagen ISO
que descargamos.

Una vez que tengamos esto, vamos a ir a donde dice **Hardware** y aquí vamos a asignar una **memoria RAM** para esta máquina virtual. Y vamos a
asignarle una cantidad de **Procesadores**.

Linux no es un sitema operativo que es muy demandante en cuestión de recursos del sistema, así que con 2GB de RAM va a andar más que bien.
Esto igualmente va a depender de nuestro sistema operativo.

Luego, en **Disco duro**, vamos a asignarle un tamaño de disco duro. Esto va a depender mucho de que aplicaciones vayamos a instalar.

Vamos a darle clic en **Terminar** y ya tenemos creada la máquina virtual.

### Configuración recomendada

- 4GB de RAM
- 2 Procesadores
- 50 GB Disco duro

### Mi configuración

- 4GB de RAM
- 2 Procesadores
- 55 GB Disco duro

Luego, vamos a ir aquí en **Configuración**, en **Red** y aquí vamos a elegir el **Adaptador puente** y aquí vamos a elegir nuestra tarjeta de
red.

```plaintext
Conectado a: Adaptador puente
Nombre: /*Nuestra tarjeta de red*/
```

Le damos en **Aceptar** y aquí vamos a tener la máquina virtual ya creada y configurada.

## Iniciar máquina virtual y configurar Kali Linux

Vamos a darle clic aquí en **Iniciar** y aquí va a estar iniciando la máquina virtual.

Le damos **Enter** en **Graphical Install** para entrar al menú de instalación del Kali Linux.

Elegimos un idioma en **Select a Language**.

Elegimos el país en **Seleccione su ubicación**.

El teclado en **Configure el teclado**.

### Configurar la red

- El nombre de la máquina. Por defecto es **kali**.
- Nombre de dominio (opcional).

### Configurar usuarios y contraseñas

- Nombre completo para el nuevo usuario
- Nombre de usuario para la cuenta
- Contraseña

### Particionado de discos

En el video se escoge: **Guiado - utilizar todo el disco**.

Mi opción: **Manual**.

Mi configuración:

| Tamaño  | Utilizar como | Punto de monataje |
| ------- | ------------- | ----------------- |
| 2 GB    | ext4          | /boot             |
| 3 GB    | intercambio   | intercambio       |
| 54.1 GB | btrfs         | /                 |

### Selección de programas

Opciones por defecto.

### Instalando el cargador de arranque GRUB

**¿Desea instalar el cargador de arranque GRUB en su unidad principal?**
Sí

**Dispositivo donde instalar el cargador de arranque:**
/dev/sda

Le vamos a dar clic en **Continuar** una vez que ya se finalizó la instalación para reiniciar el sistema Kali Linux.

## Iniciar Kali Linux

Iniciamos con el usuario y contraseña que establecimos al momento de instalarlo, le damos a **Iniciar sesión** y tendremos la máquina Kali
Linux funcionando.

---

## Otras configuraciones

### Habilitar usuario root en Kali Linux

Ingresamos el siguiente comando:

```bash
sudo su
```

Tanto `sudo` como `su` se utilizan para ejecutar comandos con permisos de root, la principal diferencia entre los dos, es la contraseña que
requieren.
Mientras `sudo` requiere la contraseña del usuario actual, `su` requiere que ingrese la contraseña del usuario root.

Al ejecutar el comando `su` anteponiendo `sudo`, el sistema solo nos pedirá que ingresemos la contraseña del usuario actual. Una vez hecho
esto, el comando `su` se ejecutará como root. Lo que significa que no necesitaremos la contraseña del usuario root.

Una vez que nos hayamos logeado, vamos a habilitar esta cuenta. Para eso, vamos a configurar la contraseña manualmente y vamos a utilizar el
comando:

```bash
passwd root
```

Lo que nos permitirá cambiar la contraseña del usuario, en este caso, el usuario root. Colocamos la contraseña que queramos dos veces, y listo, ya
podremos acceder a la cuenta root en nuestro sistema.

Ahora, o bien reiniciamos nuestro sistema o cerramos la sesión actual. Y en vez de logearnos como nuestro usuario normal, vamos a logearnos como

con el usuario root y la contraseña que colocamos anteriormente.
