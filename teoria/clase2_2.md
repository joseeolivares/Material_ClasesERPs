# Introducción al scripting en bash

## Variables

Permiten almacenar información que a lo largo del script puede cambiar.

### Ejemplo: Declaración e inicialización de una variable en un script bash:

```sh
#!/bin/bash
var="FOO"
# Se accede a las variables usando $
echo $var

```

La ejecución se hace, tras darle permisos de ejecución al script con extensión .sh, usando su ruta relativa con **./**

## Parámetros: Paso de información a nuestros scripts

Del mismo modo que podemos pasarle información a un comando (Ej: mkdir nombreDirectorio, siendo nombre directorio el parámetro), podemos pasar parámetros o argumentos a nuestros scripts en bash

### Veamos un ejemplo:

```sh
#!/bin/bash
#Los parametros se representan con $ y su posición
echo "Hola $1"

```

### ¿Qué pasa si intento usar $0?

## Condicional

Cuando queremos comprobar, una única vez, una condición, usamos la instrucción if.

### Veamos un ejemplo:

```sh
#!/bin/bash

# Definir una variable
numero=5

# Comprobar si la variable es igual a un número específico (por ejemplo, 5)
if [ "$numero" -eq 5 ]; then
    echo "La variable es igual a 5."
else
    echo "La variable no es igual a 5."
fi

```

### Otro ejemplo:

```sh
#!/bin/bash

# Verificar si se proporcionó un argumento
if [ $# -ne 1 ]; then
    echo "Uso: $0 <nombre>"
    exit 1
fi

# Saludar al nombre
echo "Hola $1"

```

### Busca los operadores de comparación

### Busca para qué sirve la instrucción "exit 1"

## Bucles

Se usan para repetir código.

### Veamos un ejemplo: Bucle for (usado para repetir algo un número fijo de veces)

```sh
#!/bin/bash

# Bucle para mostrar los números del 1 al 10
echo "Números del 1 al 10:"
for ((i = 1; i <= 10; i++)); do
    echo "$i"
done

# Línea en blanco para separar los resultados
echo

# Bucle para mostrar los números del 10 al 1
echo "Números del 10 al 1:"
for ((i = 10; i >= 1; i--)); do
    echo "$i"
done

```

### Veamos otro ejemplo: Bucle while (usado para repetir algo que depende de una condición)

```sh
#!/bin/bash

# Imprimir números del 1 al 10 con un bucle while
echo "Números del 1 al 10:"
i=1
while [ $i -le 10 ]; do
    echo $i
    i=$((i+1))
done

# Línea en blanco para separar los resultados
echo

# Imprimir números del 10 al 1 con un bucle while
echo "Números del 10 al 1:"
i=10
while [ $i -ge 1 ]; do
    echo $i
    i=$((i-1))
done

```

### ¿Existen más bucles en bash?
