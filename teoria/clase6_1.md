# Ejemplos de pipes y redireccionamientos

## Pipes

Se usa la barra vertical y sirve para comunicar comando o llamadas de tal manera que el comando o llamada de la izquierda le pasa por la "tubería" el resultado al de la derecha.

## 1. Contar líneas en un archivo:

Puedes usar el comando cat para mostrar el contenido de un archivo y luego usar un tubo para pasar la salida a wc -l para contar las líneas:

```
cat archivo.txt | wc -l

```

## 2. Búsqueda de archivos en un directorio:

Puedes usar find para buscar archivos y luego pasar los resultados a grep para buscar una cadena específica:

```
find /home/davinia -type f | grep *.txt

```

## 3. Ordenar y mostrar los 10 primeros resultados:

Puedes usar ls para listar archivos en un directorio, pasar la salida a sort para ordenarla y luego usar head para mostrar los 10 primeros resultados:

```
ls / | sort | head -n 10

```

## 4. Procesar archivos en un directorio:

En este ejemplo vamos a usar un script.

Puedes utilizar un bucle for para procesar archivos en un directorio uno por uno y aplicar una acción a cada uno. Por ejemplo, puedes buscar archivos .txt y contar las líneas en cada archivo:

```sh
for archivo in /home/*.txt; do
    cat "$archivo" | wc -l
done
```

## 5. Filtrar y procesar datos:

Puedes utilizar pipes para filtrar y procesar datos en un script. Por ejemplo, puedes buscar líneas en un archivo que contengan una palabra específica y luego guardar esas líneas en un nuevo archivo:

```
cat archivo_original.txt | grep rojo > archivo_filtrado.txt

```

En este caso usamos también redireccionamiento con el **>**

## 6. Redirigir la salida de un script a otro script:

Puedes usar un pipe para redirigir la salida de un script a otro. Esto es útil para dividir la funcionalidad en varios scripts más pequeños y reutilizables:

- script1.sh:

```sh

#!/bin/bash

for ((i=1; i<=10; i++)); do
    echo $i
done


```

- script2.sh

```sh

#!/bin/bash

while read -r numero; do
    resultado=$((numero * 2))
    echo "El doble de $numero es $resultado"
done

```

- Llamada con pipes:

```
./script1.sh | ./script2.sh

```

- Llamada con pipes y redireccionamiento:

```
./script1.sh | ./script2.sh > resultado.txt

```
