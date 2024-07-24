# Práctica de Administración y Scripting en Ubuntu

## Objetivo de la Práctica:

Reforzar y aplicar conocimientos sobre comandos de Ubuntu, incluyendo scripting en Bash para automatizar tareas.

### Apartado 1: Creación de de Directorios

- Crea un directorio llamado "PracticaUbuntu".

- Dentro de "PracticaUbuntu", crea tantos subdirectorios como el usuario quiera usando un script que reciba como parátro 1 el número de subdirectorios y luego los nombres de cada uno

- Crea un fichero dentro de cada uno que contenga el resultado de un comando.

- Ejemplo:

```
./apartado1.sh 2 Documentos Informes

PracticaUbuntu/Documentos: tendrá dentro documentos.txt con el resultado de hacer un ls
PracticaUbuntu/Informes: tendrá dentro informes.txt con el resultado de hacer un pwd

LOS COMANDOS CUYA SALIDA GUARDAMOS EN LOS txt SON DE NUESTRA ELECCIÓN

```

### Apartado 2: Creación de Archivos y Registro de Historial

- Crea un archivo de texto llamado "notas.txt" utilizando el comando touch.

- Escribe una nota en "notas.txt" utilizando nano.

- Ejecuta el comando history para ver tu historial de comandos.

- Redirige el historial de comandos a un archivo llamado "historial.txt".

### Apartado 3: Automatización de Copias de Seguridad

- Crea un script Bash llamado "backup.sh" que realice copias de seguridad de los archivos de una carpeta elegida por el usuario a un directorio "Backup".

- Programa la ejecución diaria del script utilizando **cron**

[AYUDA_CRON] (https://guias.donweb.com/guia-completa-de-cron-job-en-linux/)

- Verifica que el script funcione correctamente programando su ejecución.

### Apartado 4: Búsqueda y Filtrado de Archivos

- Utiliza el comando locate para buscar archivos con una extensión específica (por ejemplo, ".jpg", descarga algunas imáganes para que obtengas resultados).

- Utiliza grep para buscar una palabra o frase en uno de los archivos encontrados por locate.

- Redirige los resultados de búsqueda a un archivo llamado "resultados.txt".

### Apartado 5: Documentación y Presentación

- Documenta y resume los pasos y comandos utilizados en cada apartado.

- Prepara una breve presentación para compartir con el grupo y discutir los resultados.
