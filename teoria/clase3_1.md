# locate, find, grep, man y leer de teclado

## locate

Sirve para localizar ficheros en el sistema.

Además, si añades el argumento -i, desactivará la distinción entre mayúsculas y minúsculas, por lo que podrás buscar un archivo aunque no recuerdes su nombre exacto.

Para buscar contenidos que contengan dos o más palabras, utiliza un asterisco (\*). Por ejemplo:

```
locate -i escuela*nota

```

El comando buscará los archivos que contengan las palabras escuela y nota, tanto si utilizan mayúsculas como minúsculas.

## find

Sirve buscar archivos dentro de un directorio específico y realizar operaciones posteriores. Ésta es la sintaxis general:

```
find [opción] [ruta] [expresión]
```

Por ejemplo, quieres buscar un archivo llamado notas.txt dentro del directorio inicio y sus subcarpetas:

```
find /inicio -name notas.txt
```

Aquí tienes otras variaciones al utilizar find:

```
find -name nombredearchivo.txt => para buscar archivos en el directorio actual.
find ./ -type d -name nombredeldirectorio => para buscar directorios.
```

## grep (Globally search for Regular Expression and Print out)

Permite encontrar una palabra buscando entre todos los textos de un archivo específico.

Una vez que el comando grep encuentra una coincidencia, imprime todas las líneas que contienen el patrón específico. Este comando ayuda a filtrar archivos de registro de gran tamaño.

Por ejemplo, si deseas buscar la palabra azul en el archivo notepad.txt:

```
grep azul notepad.txt

```

La salida del comando mostrará las líneas que contengan azul del archivo notepad.txt.

### ¿Cómo puedo combinar grep con otros comandos?

## man

Proporciona un manual de usuario de cualquier comando o utilidad que pueda ejecutar en Terminal, incluyendo el nombre, la descripción y las opciones.

Consta de nueve secciones.

Para visualizar el manual completo, introduce:

```
man [nombre_comando]
```

Por ejemplo, si quieres acceder al manual del comando ls:

```
man ls
```

## Script ejemplo leer de teclado

```sh
#!/bin/bash

# Solicitar al usuario que inserte su nombre
echo "Por favor, inserta tu nombre:"
read nombre

# Saludar al usuario
echo "Hola, $nombre. ¡Bienvenid@!"
```
