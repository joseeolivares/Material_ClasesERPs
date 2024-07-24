# Soluciones apartado 1 Práctica

## Solución 1:

```sh

#!/bin/bash

# Verifica si se proporciona el número correcto de argumentos
if [ "$#" -lt 2 ]; then
    echo "Uso: $0 <número_de_subdirectorios> <nombre_subdirectorio1> <nombre_subdirectorio2> ..."
    exit 1
fi

# Crea el directorio "PracticaUbuntu"
mkdir -p PracticaUbuntu

# Número de subdirectorios
num_subdirectorios=$1
shift

# Itera sobre los nombres de los subdirectorios y los crea
for ((i=0; i<num_subdirectorios; i++)); do
    subdirectorio="$1"
    mkdir -p "PracticaUbuntu/$subdirectorio"
    shift

    # Crea un archivo dentro de cada subdirectorio con el resultado de un comando
    comando="ls -l"
    resultado_comando=$(eval "$comando")
    echo "$resultado_comando" > "PracticaUbuntu/$subdirectorio/resultado.txt"
done


```

## Solución 2:

```sh
#!/bin/bash

# Verifica si se proporciona el número correcto de argumentos
if [ "$#" -lt 2 ]; then
    echo "Uso: $0 <número_de_subdirectorios> <nombre_subdirectorio1> <nombre_subdirectorio2> ..."
    exit 1
fi

# Crea el directorio "PracticaUbuntu"
mkdir -p PracticaUbuntu

# Número de subdirectorios
num_subdirectorios=$1
shift

# Itera sobre los nombres de los subdirectorios y los crea
for subdirectorio in "$@"; do
    mkdir -p "PracticaUbuntu/$subdirectorio"

    # Crea un archivo dentro de cada subdirectorio con el resultado de un comando
    comando="ls -l"
    resultado_comando=$(eval "$comando")
    echo "$resultado_comando" > "PracticaUbuntu/$subdirectorio/resultado.txt"
done

```

## Solución 3:

```sh

#!/bin/bash

# Verifica si se proporciona el número correcto de argumentos
if [ "$#" -lt 2 ]; then
    echo "Uso: $0 <número_de_subdirectorios> <nombre_subdirectorio1> <nombre_subdirectorio2> ..."
    exit 1
fi

# Crea el directorio "PracticaUbuntu"
mkdir -p PracticaUbuntu

# Número de subdirectorios
num_subdirectorios=$1

# Itera sobre los nombres de los subdirectorios y los crea
for subdirectorio in "${@:2}"; do
    mkdir -p "PracticaUbuntu/$subdirectorio"

    # Crea un archivo dentro de cada subdirectorio con el resultado de un comando
    comando="ls -l"
    resultado_comando=$(eval "$comando")
    echo "$resultado_comando" > "PracticaUbuntu/$subdirectorio/resultado.txt"
done

```

## Solución 4:

```sh

#!/bin/bash

# Verifica si se proporciona el número correcto de argumentos
if [ "$#" -lt 2 ]; then
    echo "Uso: $0 <número_de_subdirectorios> <nombre_subdirectorio1> <nombre_subdirectorio2> ..."
    exit 1
fi

# Crea el directorio "PracticaUbuntu"
mkdir -p PracticaUbuntu

# Número de subdirectorios
num_subdirectorios=$1

# Contador inicializado en 0
contador=0

# Itera sobre los nombres de los subdirectorios y los crea
for subdirectorio in "$@"; do
    ((contador++))
    # Comprobamos contador
    if [ $contador -gt 1 ]; then
	    mkdir -p "PracticaUbuntu/$subdirectorio"

	    # Crea un archivo dentro de cada subdirectorio con el resultado de un comando
	    comando="ls -l"
	    resultado_comando=$(eval "$comando")
	    echo "$resultado_comando" > "PracticaUbuntu/$subdirectorio/resultado.txt"
    fi
done
```

## Solución 5: Johan

```sh
#!/bin/bash
var1=PracticaUbuntu
comandos=(p ls pwd history)
arg=($@)
numpara=$1
((numpara++))

echo $var1
echo ${comandos[*]}
echo $numpara
echo ${arg[*]}

if [ $# -eq $numpara ]; then
	mkdir /home/johann/clase5_2/$var1
	echo "Carpeta $var1 creada"
	for (( i=1 ; i <=$1 ; i++ )); do
		mkdir /home/johann/clase5_2/$var1/${arg[i]}
		echo "Se creo directorio ${arg[i]}"
		${comandos[i]} /home/johann/clase5_2/ > /home/johann/clase5_2/$var1/${arg[i]}/$i.txt
		echo "Se creo archivo con el comando ${comandos[i]}"
	done
else
	echo "Error de Syntaxis: $0 [NumeroDirectorios] [Nombre1] [Nombre2]..."
fi
```
