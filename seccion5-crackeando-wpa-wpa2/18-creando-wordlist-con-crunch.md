# 18. Creando Wordlist con Crunch

Vamos a ver cómo hacer diccionarios de fuerza bruta.

## Diccionarios de fuerza bruta

Porque como dijimos, nosotros, para hacer el ataque de fuerza bruta, tenemos que tener una lista de contraseñas, una lista de posibles
usuarios. Una lista en la cual vamos a probar y ver si nos da, si tenemos el resultado correcto o no.

Normalmente se hace con contraseñas y vamos a hacerlo con contraseña.

Vamos a intentar sacar la contraseña de lo que vendría siendo el, vamos a intentar sacar la contraseña de un servicio FTP.

¿Cómo podemos hacer ataques, diccionarios de contraseñas? Podemos utilizar `crunch`.

## Uso de crunch

Si hacemos un:

```bash
man crunch
```

Que es para desplegar un manual.

Es una herramienta que genera wordlist poniendo cual queremos que sea el mínimo de caracteres y cual queremos que sea el máximo, y podemos usar
una sucesión de caracteres.

Por ejemplo, queremos hacer un diccionario para un ataque de contraseñas que sea de `2` a `4` caracteres y que tenga los números `1234`:

```bash
crunch 2 4 1234
```

Acá se va a estar generando lo que vendría siendo estas posibles contraseñas.
**Podemos guardar esas posibles contraseñas en un archivo de texto**. 

Estas posibles contraseñas que pueden ser y probar combinaciones, el uno
lo pone acá y prueba posibles combinaciones que se pueden hacer con estos
caracteres que se dieron.

Podemos hacer el diccionario así, podemos agregar caracteres como números, como letras:

```bash
crunch 2 4 1234456789 abc
```

Y acá se va a estar generando el diccionario. Esto es una herramienta para generar diccionarios de fuerza bruta.

También hay una que se llama `Cupp`, que lo que hace es que podamos generar diccionarios de fuerza bruta personalizados.