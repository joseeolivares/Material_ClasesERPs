# Ejercicios Resueltos

## Ejercicio 8

```sh

#!/bin/bash

# Asigna los enteros a las variables
entero1=10
entero2=20

# Compara los enteros y muestra el mayor
if [ "$entero1" -gt "$entero2" ]; then
    echo "El mayor es $entero1"
elif [ "$entero2" -gt "$entero1" ]; then
    echo "El mayor es $entero2"
else
    echo "Los enteros son iguales"
fi

```

## Ejercicio 9

```sh
#!/bin/bash

# Verifica si se proporciona un nombre de directorio como parámetro
if [ $# -eq 0 ]; then
    echo "Por favor, proporciona un nombre de directorio como parámetro."
    exit 1
fi

# Obtén el nombre de directorio proporcionado como parámetro
nombre_directorio="$1"

# Ruta completa del directorio en /home
ruta_directorio="/home/$nombre_directorio"

# Verifica si el directorio ya existe
if [ -d "$ruta_directorio" ]; then
    echo "El directorio \"$nombre_directorio\" ya existe en /home."
else
    # Crea el directorio en /home
    mkdir "$ruta_directorio"
    echo "Se ha creado el directorio \"$nombre_directorio\" en /home."
fi

```

## Ejercicio 10

```sh
#!/bin/bash

# Usuario y contraseña correctos (definidos en variables)
usuario_correcto="usuario"
contrasena_correcta="contrasena"

# Verifica si se proporcionan dos parámetros (usuario y contraseña)
if [ $# -ne 2 ]; then
    echo "Por favor, proporciona un nombre de usuario y una contraseña como parámetros."
    exit 1
fi

# Obtiene el nombre de usuario y la contraseña proporcionados como parámetros
usuario_ingresado="$1"
contrasena_ingresada="$2"

# Compara el nombre de usuario y la contraseña con los valores correctos
if [ "$usuario_ingresado" = "$usuario_correcto" ] && [ "$contrasena_ingresada" = "$contrasena_correcta" ]; then
    echo "Acceso concedido. Bienvenido, $usuario_correcto."
else
    echo "Acceso denegado. Usuario o contraseña incorrectos."
fi

```
