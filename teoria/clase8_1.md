# Ejercicios 11 a 13 resueltos

## 11

```sh

#!/bin/bash

# Verificar el número de argumentos
if [ $# -lt 2 ]; then
    echo "Uso: $0 <opción> <argumento>"
    exit 1
fi

# Comprobar si la opción es 1 para mostrar el ls de una ruta (si es un directorio)
if [ $1 -eq 1 ]; then
    if [ -d "$2" ]; then
        ls -l "$2"
    else
        echo "El argumento no es un directorio válido."
        exit 1
    fi

# Comprobar si la opción es 2 para mostrar el cat de un archivo
elif [ $1 -eq 2 ]; then
    if [ -f "$2" ]; then
        cat "$2"
    else
        echo "El argumento no es un archivo válido."
        exit 1
    fi

# Opción no válida
else
    echo "Opción no válida. Las opciones válidas son 1 para mostrar ls de un directorio y 2 para mostrar cat de un archivo."
    exit 1
fi

```

## 12

```sh
#!/bin/bash

# Verificamos si se proporcionó un argumento
if [ $# -eq 0 ]; then
    echo "Debe proporcionar un número entre 1 y 5 como argumento."
    exit 1
fi

# Verificamos si el argumento es un número válido
if ! [[ "$1" =~ ^[1-5]$ ]]; then
    echo "El número proporcionado debe estar entre 1 y 5."
    exit 1
fi

# Iteramos para crear los archivos
for ((i = 1; i <= $1; i++)); do
    touch "${i}.txt"
    echo "Archivo ${i}.txt creado."
done

```

## 13

```sh
#!/bin/bash

# Verificamos si se proporcionaron dos argumentos
if [ $# -ne 2 ]; then
    echo "Debe proporcionar exactamente dos números como argumentos."
    exit 1
fi

# Verificamos si los argumentos son números enteros
if ! [[ "$1" =~ ^[0-9]+$ ]] || ! [[ "$2" =~ ^[0-9]+$ ]]; then
    echo "Ambos argumentos deben ser números enteros."
    exit 1
fi

# Verificamos si el primer número es menor o igual al segundo
if [ "$1" -gt "$2" ]; then
    echo "El primer número debe ser menor o igual al segundo."
    exit 1
fi

# Mostramos los números en el intervalo
echo "Los números en el intervalo [$1, $2] son:"
for ((i = $1; i <= $2; i++)); do
    echo "$i"
done

```
