# Primeros Comandos

## sudo

Abreviatura de superusuario do, sudo es uno de los comandos básicos más populares de Linux que te permite realizar tareas que requieren permisos administrativos o de root.

Al utilizar sudo, el sistema pedirá a los usuarios que se autentiquen con una contraseña. A continuación, el sistema Linux registrará una marca de tiempo como seguimiento. Por defecto, cada usuario root puede ejecutar comandos sudo durante 15 minutos por sesión.

Si intentas ejecutar sudo en la línea de comandos sin autenticarte, el sistema registrará la actividad como un evento de seguridad.

## history

Con history, el sistema mostrará hasta 500 comandos ejecutados previamente (esto es configurable, es decir, se pueden ver más o menos, ya que se guardan en un fichero del sistema), permitiéndote reutilizarlos.

Ten en cuenta que sólo los usuarios con privilegios sudo pueden ejecutar este comando.

## pwd (print working directory)

Utiliza el comando pwd para mostrar la ruta de tu directorio de trabajo actual (imprimir el directorio de trabajo). Es muy útil cuando nos estamos moviendo por diferentes rutas dentro de nuesto Linux.

## cd (change directory)

Para navegar por los archivos y directorios de Linux (cambiar de directorio), usa el comando cd. Necesita que le especifiques la ruta a la que quieres accder

Supongamos que estás en /home/nombredeusuario/Documentos y deseas ir a Fotos, un subdirectorio de Documentos. Para hacerlo, simplemente escribe el siguiente comando:

```
cd Fotos

```

Otro escenario es si deseas ir a un directorio completamente diferente al que te encuentras, por ejemplo, /home/nombredeusuario/Peliculas. En este caso, debes escribir cd seguido de la ruta absoluta del directorio:

```
cd /home/nombredeusuario/Peliculas

```

## ls (list)

El comando ls se usa para ver el contenido de un directorio (listar). Por defecto, mostrará el contenido de tu directorio actual.

Si deseas ver el contenido de otros directorios, escribe ls y luego la ruta del directorio que deseas consultar.

Por ejemplo, para ver el contenido de un directorio Documentos, que se encuentra en esta ruta **/inicio/nombredeusuario/Documentos**, haríamos:

```
ls /inicio/nombredeusuario/Documentos

```

## mkdir (make directory)

Sirve para crear uno o varios directorios a la vez (hacer un directorio) y establecer los permisos para cada uno de ellos.

El usuario que ejecuta este comando debe tener el permiso para crear una nuevo directorio en el directorio principal o puede recibir un error de permiso denegado.

Por ejemplo:

```
mkdir Musica

mkdir Musica/Canciones

```

## touch

Es utilizado para cambiar la fecha y hora de última modificación de un archivo. También puede utilizarse para crear un archivo vacío.

Por ejemplo si queremos crear o cambiar la marca de tiempo de un fichero Web.html dentro de **/inicio/nombredeusuario/Documentos**, se haría:

```
touch /inicio/nombredeusuario/Documentos/Web.html

```

## Primer script Bash: Hola Mundo

Lo primero que tenemos que hacer es crear **holaMundo.sh** con el siguiente contenido:

```
#!/bin/bash
# Script de hola mundo
echo "hola mundo"

```

### Partes que lo componen:

1. **#**: Sirve para escribir comentarios.

2. **#!/ruta/de/interprete**: Sirve para llamar a nuestro interprete, como perl, bash, sh, python, etc, y se usa para los lenguajes interpretados, de modo que se ejecuten con el intérprete que corresponde.

3. **echo**: Sirve para mostrar información por la terminal.

En las siguientes clases, veremos la ejecución.
