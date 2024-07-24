# Ejercicios

## 14

Indica qué hace este script:

```sh
#!/bin/bash

directorio="/ruta/al/directorio"

cadena_a_buscar="texto_a_buscar"

archivos_txt=$(find "$directorio" -type f -name "*.txt")

for archivo in $archivos_txt; do
    if grep -q "$cadena_a_buscar" "$archivo"; then
        echo "Cadena encontrada en el archivo: $archivo"
        grep "$cadena_a_buscar" "$archivo"
        echo "----------------------------------------"
    fi
done

```

## 15

Averigua la utilidad del | en el uso de la terminal y pon un ejemplo.

## 16

Modifica el script del ejercicio 14 de manera que permitas que el usuario pase por parámetros tanto el directorio como el texto que quirere buscar con grep.

## 17

Diseña un script que realice lo siguiente:

1. Crea un directorio llamado "mis_archivos".
2. Dentro de "mis_archivos", crea dos archivos llamados "archivo1.txt" y "archivo2.txt".
3. Cambia los permisos de "archivo1.txt" para que sea de solo lectura.
4. Cambia los permisos de "archivo2.txt" para que sea de lectura y escritura.
5. Muestra los permisos actualizados de ambos archivos.

## 18

Diseña un script que realice lo siguiente:

1. Busca todos los archivos con extensión ".txt" en el directorio actual utilizando el comando find (crea algunos, si no dispones de ellos).
2. Muestra una lista de los nombres de estos archivos.
3. Utiliza el comando **wc** (usa man para ver su manual) para contar la cantidad de líneas en cada archivo y mostrar el número total de líneas en todos los archivos.

## 19

Diseña un script que realice lo siguiente:

1. Utilza el comando sudo para instalar un programa de tu elección utilizando apt-get. Por ejemplo, puedes instalar "tree" con sudo apt-get install tree.
2. Luego, espera la entrada del usuario para continuar, indícale que ya se ha instalado y que como es una pruba debe pulsar enter para desinstalar.
3. Una vez que el usuario presiona Enter, utiliza sudo apt-get remove para desinstalar el programa.

## 20

Realiza un script en bash, que permita crear un fichero y asignar los permisos que queramos, la ejecución va a ser así:

```
./fichero_permisos.sh nombre.txt rwx rw r

Esto indicará que el fichero se va a llamar nombre.txt y va a tener permisos de lectura, escritura y ejecución para el propietario, de lectura y escritura para el grupo y de lectura para el resto.

```
