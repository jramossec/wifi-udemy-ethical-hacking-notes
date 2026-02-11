# 5. Comandos básicos de Linux

Vamos a hacer hincapié en los comandos básicos de Linux para poder manejarnos por una terminal.

La **terminal** es una consola en la cual nosotros lo que hacemos es ingresar comandos y mediante estos comandos nosotros podemos manejarnos
por la computadora.

Antes de que existan interfaces gráficas como las que conocemos ahora, había que manejarse a través de una consola.

Nosotros, para poder ejecutar herramientas de hacking para poder ejecutar diversos programas, vamos a hacerlo a través de la terminal. Y
no solo para ejecutar estas herramientas de hacking, sino también para ejecutar diversas herramientas y aplicaciones se hace a través de la
consola.

## ls

`ls` Este comando lo que hace es enumerarnos las carpetas o directorios en los cuales la carpeta de directorios en donde estamos ahora.

## cd (change directory)

Con el comando `cd` lo que hacemos es que podemos ingresar un directorio, podemos ingresar una carpeta. Ejemplo:

```bash
cd Descargas
```

Y lo que hicimos acá es movernos a la carpeta de Descargas.

Si nosotros queremos movernos al directorio anterior, a la carpeta anterior, lo que hacermos es:

```bash
cd ..
```

## pwd (print working directiry)

Vamos a ver en qué carpeta estamos.

## cat (catenate)

Este comando se utiliza para ver el contenido de un archivo o para poder crear un archivo en el cual podemos escribir.

### Ejercicio

Crear un archivo en **Escritorio**, vamos a darle clic derecho, **Crear un documento**, **Archivo vacío**. Vamos a llamarlo **documento** a este
archivo, vamos a darle **Crear** y vamos a escribir algo adentro de este documento, vamos a poner `Hola Mundo`.

Nos vamos a **Archivo**, **Guardar como...**, **Guardar**, **Reemplazar**.

Para ver el contenido que hay adentro de este archivo vamos a poner el comando:

```bash
cat documento
```

Y esto imprimirá `Hola Mundo` en la terminal.

## mkdir (make directory)

Se utiliza para crear directorios, para crear carpetas.

## Ejercicio

Vamos a crear una carpeta llamada **Carpeta**, ponemos el comando `mkdir` y el nombre que le queremos poner a la carpeta nueva:

```bash
mkdir Carpeta
```

Y si hacemos un `ls` podemos ver que tenmos una nueva carpeta llamada `Carpeta`.

## rmdir (remove directory)

Y si nosotros queremos eliminar una carpeta, vamos a eliminar la carpeta
que acabamos de crear.
Vamos a poner `rmdir` y vamos a poner el nombre de la carpeta que
queremos eliminar. En este caso, se llama **Carpeta** el nombre:

```bash
rmdir Carpeta
```

Si hacemos un `ls` de vuelta, podemos ver que desapareció la carpeta que
habíamos creado anteriormente con el comando `mkdir`.

## touch

Comando que nos sirve para poder crear un archivo simple con el nombre y la extensión que nosotros queramos. Vamos a poner `touch` y el nombre del
archivo:

```bash
touch documento1.txt
```

En este caso estamos aclarando que vamos a crear un archivo que se llame **documento1** y que tenga la extensión `.txt`. Que tenga la extensión
`.txt` va a hacer referencia a que es un archivo de texto y el sistema lo va a interpretar como un archivo de texto.

Si hacemos un `ls` aquí tenemos este archivo en la carpeta actual, en el directorio actual llamado **documento1.txt**.

## rm (remove)

Lo que hacemos es eliminar archivos.

Vamos a eliminar el archivo que creamos recientemente llamado **documento1.txt**.

```bash
rm documento1.txt
```

Si hacemos un `ls` de vuelta vamos a ver de que este archivo ya no está más en el sistema. Es decir, que lo eliminamos recientemente con el
comando `rm` que es **remove**.

## cp (copy)

Copiar un archivo.

### Ejercicio

Vamos a crear un archivo con el comando `touch`:

```bash
touch documento1.txt
```

Hacemos un `ls`, verificamos que lo tenemos aquí el documento. Si queremos copiarlo este documento vamos a utilizar el comando **copy** y
vamos a copiar este archivo **documento.txt** y vamos a copiarlo al **Escritorio**:

```bash
cp documento1.txt /home/{my-user}/Escritorio
```

Veremos que tenemos el archivo llamado **documento1.txt** que se copió al **Escritorio** pero sigue estando en el directorio actual, la carpeta
actual.

## mv (move)

Sirve para mover, en este caso el documento o archivo. Con el comando `mv` vamos a poner el nombre del archivo que queremos mover, en este caso
es **documento1.txt** y tenemos que indicar la ruta completa hacia donde lo queremos mover:

```bash
mv documento1.txt /home/{my-user}/Escritorio
```

Esto moverá el **documento1.txt** al **Escritorio** y si verificamos no está más en la carpeta actual.

Con el comando `mv` lo que hacemos es que movemos archivos de un lugar a otro.

## clear

Este comando se utiliza para limpiar la terminal. Nos limpia los comandos anteriores que habíamos ingresado.

---

Estos son los comandos principales que se utilizan en un sistema Linux. Hay muchísimos más comandos en Linux, pero estos son los comandos más
básicos y los que se utilizan con mayor frecuencia.

Existen comandos que sirven para matar procesos, comandos para darle permisos a un archivo, a una carpeta. Comandos que sirven para, por
ejemplo, encontrar texto dentro de un archivo. También comandos que nos permiten descargar archivos desde una URL de una página web a través de
una terminal, entre otros.