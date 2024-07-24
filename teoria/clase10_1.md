# Introducción a usuarios y grupos.

## Acciones sobre los usuarios

### Añadir un nuevo usuario

Vamos a ver cómo podemos añadir un usuario por comandos, debes utilizar el comando **adduser**, con un **sudo** delante, dado que la acción requiere de permisos de superusuario.

Algo importante a tener en cuenta, al crear un nuevo usuario, **también se creará un nuevo grupo con el mismo nombre**, dentro del cual se va a incluir este usuario.

A continuación tienes la sentencia básica. Verás que al hacer esto, el sistema **te pedirá una serie de detalles sobre el usuario, como la contraseña de Unix o el nombre completo de usuario**. Puedes omitir el resto de datos.

```
sudo adduser usuario
```

### Eliminar usuario

En este caso el comando a utilizar es **userdel**.

Al eliminar el usuario, si este estaba dentro de un grupo donde solo estaba él, el grupo también se borrará.

No pide información, nos elimina el usuario directamente

```
sudo userdel usuario
```

### Cambiar la contraseña de una cuenta

Esta acción que puede resultar necesaria, se realiza con la instrucción **passwd**

```
sudo passwd usuario
```

### Ver todos los usuarios del sistema

En Linux, toda la información relativa a los usuarios es almacenada en un archivo de texto. Este archivo es **/etc/passwd**. Mediante este archivo también podrás editar sus propiedades, aunque lo recomendable esutilizarlo únicamente a modo informativo (de ahí el hecho de no abrirlo con sudo en el ejemplo de abajo), y utilizar los comandos apropiados en caso de querer modificar algo.

Si quieres listar todos lo usuarios a través de la consola, tan solo debes leer el contenido del ficheroLas contraseñas obviamente no se muestran en texto plano en este archivo, sino que van protegidas por hash aparte.

```
cat /etc/passwd
```

### Ver con qué usuario estoy conectado

Puede que hayamos realizado varios login y que no sepamos con qué usuario estamos conectados, para solucionar esto se usa el comando **whoami** o visualizar la variable de bash **$USER**

```
whoami

echo $USER
```

### Conectar con un usuario por comandos y salir

Para conectar con un usuario diferente, como hemos visto, se usa **su**

Ejemplo

```
su juan => siendo juan el usuario

Una vez terminadas las acciones con juan, se sale con exit
```

## Acciones sobre los grupos

Los grupos se utilizan para permitir o restringir el acceso a ficheros y directorios de forma más sencilla que de manera individual, y evitar el tener que parametrizar cada uno de los permisos, usuario por usuario. Si tenemos una serie de cuentas que deben compartir el mismo nivel de permisos, estos pueden pertenecer al mismo grupo.

### Añadir un nuevo grupo

El comando para añadir un grupo es **groupadd**

```
sudo groupadd grupo
```

### Eliminar un grupo

Esta acción no es muy común, salvo en sistemas con muchos usuarios, la sentencia es:

```
sudo groupdel grupo
```

#### NO es recomendable borrar en ningún caso uno de los grupos, ni los usuarios creados por el sistema en la instalación inicial, a no ser que sepas muy bien lo que haces.

### Añadir un usuario dentro de un grupo

Si creamos un grupo tenemos que poder añadir usuarios a él, esto se hace de la siguiente forma:

```
sudo adduser usuario grupo
```

En Ubuntu, el root está deshabilitado. En este caso, si quieres que el nuevo usuario pueda hacer uso "sudo", necesitarás añadirlo al grupo:

```
sudo adduser usuario sudo
```

### Eliminar un usuario de un grupo

Para eliminar un usuario dentro de un determinado grupo, puedes usar de la siguiente sentencia:

```
sudo deluser usuario grupo
```

### Ver todos los grupos del sistema

En este caso se encuentran en **/etc/group**, no edites el fichero y no borres grupos creados por el sistema.

```
cat /etc/group
```

### Consultar los grupos en los que está el usuario actual

Ejecuta el comando siguiente:

```
groups
```
