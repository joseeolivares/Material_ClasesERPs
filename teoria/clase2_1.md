# Más comandos útiles

## su (switch user)

Permite ejecutar un programa como un usuario diferente. Este cambia la cuenta administrativa en la sesión de inicio de sesión actual.

Cuando se ejecuta sin ninguna opción o argumento, el comando su se ejecuta con privilegios de root. Te pedirá que te autentiques y dispondrás de permisos de root temporalmente.

## apt-get

Se trata de una una herramienta de línea de comandos de Linux para gestionar las bibliotecas de Advanced Package Tool (APT) en Linux. Permite recuperar información y paquetes de fuentes autenticadas para gestionar, actualizar, eliminar e instalar software y sus dependencias.

Para ejecutarlo **es necesario utilizar privilegios sudo o de root.**

### Esta es la sintaxis principal:

```
apt-get parametro

```

### Algunos de los parámetros más comunes que puedes añadir a apt-get:

```
update:  sincroniza los archivos del paquete desde sus fuentes.

Ej:

apt-get update

upgrade:  instala la última versión de todos los paquetes instalados, es decir actualiza.

Ej:

apt-get upgrade

install: permite instalar paquetes

Ej:

apt-get install tree

```

## rm (remove)

Se utiliza para borrar archivos dentro de un directorio. Asegúrate de que el usuario que ejecuta este comando tiene permisos de escritura, en caso contrario no podrás eliminar el fichero, salvo que cambies los permisos.

Se trata de una acción que no se puede deshacer.

### Esta es la sintaxis general:

```
rm nombredearchivo
```

## rmdir (remove directory)

Se utiliza para eliminar permanentemente un directorio **vacío**. Recuerda que el usuario que ejecuta este comando debe tener privilegios en el directorio padre.

### Esta es la sintaxis general:

```
rmdir nombrededirectorio
```

## cat (abreviatura de concatenate)

Es uno de los comandos más utilizados en Linux. Este lista, combina y escribe el contenido de los archivos en la salida estándar. Para ejecutar este comando, escribe cat seguido del nombre del archivo y su extensión.

### Por ejemplo: mostramos el contenido de un archivo así:

```
cat archivo.txt
```

### Otros ejemplos:

```
cat > nombredearchivo.txt => crea un nuevo archivo.

cat nombredearchivo1.txt nombredearchivo2.txt>nombredearchivo3.txt => fusiona nombrearchivo1.txt y nombrearchivo2.txt y almacena el resultado en nombrearchivo3.txt.

```

## cp

Comando que permite copiar ficheros o directorios de una ruta a otra:

Ejemplo:

```

    cp rutaOrigen rutaDestino

```

Ojo: puedes cambiar su nombre en el destino

## mv

Comando que permite mover ficheros o directorios de una ruta a otra:

Ejemplo:

```

    mv rutaOrigen rutaDestino

```

Ojo: puedes cambiar su nombre en el destino

## chmod

Comando que permite cambiar permisos a ficheros y directorios y que vamos a ver cómo funciona usando su versión numérica:

Veamos la siguiente tabla:

En ella podemos ver cómo usando binario, se realizan todas las combianciones de permisos de lectura (r), escritura(w) y ejecución (x) posibles.

| r   | w   | x   | Permiso |
| --- | --- | --- | ------- |
| 0   | 0   | 0   | 0       |
| 0   | 0   | 1   | 1       |
| 0   | 1   | 0   | 2       |
| 0   | 1   | 1   | 3       |
| 1   | 0   | 0   | 4       |
| 1   | 0   | 1   | 5       |
| 1   | 1   | 0   | 6       |
| 1   | 1   | 1   | 7       |

Además de esto, tenemos tres niveles de permisos:

1. Propietario
2. Grupo
3. Todos o resto de usuarios

Ejemplo: Por tanto, si queremos aplicar permisos de lectura, escritura y ejecución al propietario, lectura y escritura al grupo y ningún permiso al resto de usuarios en una ruta específica, debemos ejecutar lo siguiente:

```

    chmod 760 ruta

```

# Ejercicios

## 5

Usando el mismo esquema de directorios y ficheros que en el ejercicio 1:

- Estando en F copia a.txt a B
- Estando en C mueve a.txt a E (el que tienes en F)
- Estando en D mueve b.txt a D y cambia su nombre a nuevob.txt
- Estando en B, crea un fichero en F, usando ruta relativa

## 6

Usando el mismo esquema de directorios y ficheros que en el ejercicio 1:

- Estando en F asignar permisos de lectura al propietario, de escritura al grupo y de ejecución a todos, al fichero a.txt
- Estando en C asignar permisos de lectura y escritura al propietario, de escritura y ejecución al grupo y de lectura, escritura y ejecución a todos, al fichero b.txt
- Estando en C elimina todos los permisos al grupo y a todos y asigna todos los permisos (lectura, escritura y ejecución) al propietario en el fichero b.txt
