# Ejercicios

## 1

Indica el enunciado de este ejercicio y para qué sirve -e y en qué se diferencia con -f y -d

```sh
#!/bin/bash

archivo="mi_archivo.txt"

if [ -e "$archivo" ]
then
  echo "El archivo $archivo existe."
else
  echo "El archivo $archivo no existe."
fi
```

## 2

Indica el enunciado de este ejercicio

```sh
#!/bin/bash

directorio="/ruta/al/directorio"

for archivo in "$directorio"/*
do
  if [ -f "$archivo" ] && [[ "$archivo" == *.txt ]]
  then
    echo "Archivo encontrado: $archivo"
  fi
done
```

## 3

Indica el enunciado de este ejercicio

```sh
#!/bin/bash

numero=""
while ! [[ "$numero" =~ ^[0-9]+$ ]]
do
  read -p "Ingresa un número: " numero
done

echo "Número válido ingresado: $numero"

```

## 4

Indica el enunciado de este ejercicio

```sh
#!/bin/bash

directorio="/ruta/al/directorio"
prefijo="archivo"

contador=1

for archivo in "$directorio"/*
do
  if [ -f "$archivo" ]
  then
    nuevo_nombre="${prefijo}_${contador}.txt"
    mv "$archivo" "$directorio/$nuevo_nombre"
    echo "Renombrado $archivo a $nuevo_nombre"
    contador=$((contador + 1))
  fi
done

```

## 5

Indica el enunciado de este ejercicio

```sh
#!/bin/bash

while true
do
  echo "Procesos en ejecución:"
  ps aux
  read -p "Ingresa el PID del proceso que deseas matar (o 'q' para salir): " opcion

  if [ "$opcion" == "q" ]
  then
    break
  fi

  kill "$opcion"
  echo "Proceso con PID $opcion matado."
done


```
