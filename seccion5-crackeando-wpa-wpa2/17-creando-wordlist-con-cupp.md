# 17. Creando Wordlist con Cupp

Vamos a ver a cómo realizar diccionarios de fuerza bruta, a cómo crear diccionarios de fuerza bruta con una herramienta llamada **CUPP**.

## CUPP - Common User Passwords Profiler

Esta herramienta nos permite crear diccionarios de fuerza bruta pero personalizados, hacia nuestra víctima.

## Instalación de CUPP

Los pasos de la instalación son muy sencillos. Lo que tenemos que hacer es hacer un:

```bash
cd Escritorio
git clone https://github.com/Mebus/cupp.git
```

* Repositorio de GitHub: [CUPP](https://github.com/Mebus/cupp).

Y se va a estar clonando la herramienta.

## Uso de CUPP

Una vez que ya la tenemos clonada, vamos a hacer un:

```bash
cd cupp
```

Esto es para dirigirnos al directorio. Hacemos un `ls` y tenemos este archivo que es el que tenemos que ejecutar: `cupp.py`.

Hacemos un:

```bash
sudo python3 cupp.py -h
```

Esto para ejecutarlo como administrador y que no nos de problemas en el momento de ejecutar la herramienta. Vamos a hacer un `-h` para ver las
diferentes opciones que tenemos.

Tenemos la opción `-i`, que sirve para hacerla interactiva y pasarle argumentos de forma interactiva:

```bash
sudo python3 cupp.py -i
```

Y acá para realizar el diccionario de fuerza bruta. La fuerza bruta consiste, en un ataque de **fuerza bruta por diccionario** consiste en
probar varias contraseñas de una lista, de una wordlist, de una passlist de un diccionario y ver cuál funciona y cuál no.

Probamos varias contraseñas de una lista a las redes sociales de nuestra víctima, a un servicio, e intentamos sacar la contraseña, obtener la
contraseña por medio de este ataque, por medio de probar que contraseñas de una lista funcionan y cuál no. Las vamos a ir testeando.

Este tipo de herramientas sirve bastante porque una persona normal suele utilizar de contraseña, no sé, su nombre, apellido, su fecha de
nacimiento de cualquier persona, así que suele utilizar ese tipo de datos. Así que, cuanto más datos pongamos en esta herramienta, mejor.

Vamos a poner un **First Name**, en este caso vamos a poner cualquier nombre. En este caso, no vamos a poner el nombre de una persona.

Vamos a poner `Apellido`.

Acá nos pide un **Nickname**, nos pide diferentes datos, por ejemplo un primer nombre, un apellido y un nickname. Nickname vamos a poner `Usuario1234`.

**En el caso de nosotros**, vamos a tener que poner según la información que sacamos de la víctima, ponemos el nombre, ponemos el apellido,
ponemos el usuario.

Después nos pide acá la fecha de cumpleaños. En este caso vamos a ponerle el, no se, `25012021`, por ejemplo.

Acá nos pide **Partners) name**, que vendría siendo el nombre de los padres. Vamos a ponerle `NOmbre1`, como se dijo anteriormente, nosotros
vamos a tener que poner la información que sacamos de nuestra víctima.

Después nos pide **Partners) nickname**. En el caso que no queramos rellenar la información, le damos un Enter y se va a poner en blanco.

Bueno, vamos a saltar todo esto.

Acá nos pide si queremos agregar "key words" de la víctima. En este caso le pusimos que no. Si queremos agregarle caracteres especiales al final
de las palabras. Le podemos poner que si `y`, si queremos.

Si queremos ponerle números random al final de las palabras, en nuestro caso si `y`, vamos a ponerle que si. **Leet mode?**, que vendría siendo
reemplazar las letras por medio de números. Así que, vamos a ponerle que no `n`.

Y acá ya tenemos el diccionario guardado en un `.txt`.

Vamos a hacer un print `y` para mostrarnos todas las posibles contraseñas:

```plaintext
[hola.txt]  <password_n>
```

Esta es lo que vendría siendo la posible contraseña del diccionario que generamos. En este caso, si nosotros completamos con información de
nuestra víctima, debería mostrarnos acá el nombre de la víctima, los datos, los diferentes datos que nosotros pusimos.

Vamos a hacer un `Ctrl+C`. Si hacemos un `ls`, acá tenemos el diccionario llamado **hola .txt**. Lo vamos a cambiar de nombre:

```bash
mv hola\ .txt hola.txt
```

Ahora sí. Le cambiamos el nombre porque le sacamos este espacio que tenía.

Ahora vamos a hacer un:

```bash
cat hola.txt
```

Este vendría siendo el diccionario con las posibles contraseñas. Estas vendrían siendo las posibles contraseñas que nosotros tenemos de nuestra
víctima.

## Resumen

Esta la vamos a ir testeando para ver cuál funciona y cuál no, cuál contraseña de estas que la vamos a testear ante la víctima, vamos a ver
cuál funciona y qué contraseña no funciona.

Así que bien, hasta acá el uso de esta herramienta llamada CUPP, que únicamente y exclusivamente sirve para crear diccionarios de fuerza bruta
orientados a nuestra víctima.

Porque como vimos, que nosotros pusimos cierto tipo de información, pusimos nombres, apellidos, nickname, fecha de nacimiento, el nombre de
los padres, entre más tipo de información que nos pidió. Y en base a esa información que la herramienta obtiene, crea un diccionario de fuerza
bruta, por medio de un algoritmo que mezcla el nombre, el apellido y, no sé, una fecha de nacimiento, y va generando posibles contraseñas que las
probamos para nuestro ataque de fuerza bruta.

Y puede ser de que algunas de esas contraseñas sean correctas y pueden ser que otras no. Bueno, una va a ser correcta y las demás no.