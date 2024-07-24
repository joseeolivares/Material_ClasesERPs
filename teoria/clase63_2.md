# Ejemplo Backup Cron 

## Crear el Script backup.sh

```sh
#!/bin/bash

# Verificar si se proporcionó un directorio
if [ -z "$1" ]; then
    echo "Uso: $0 <directorio>"
    exit 1
fi

DIRECTORIO=$1
FECHA=$(date +%Y-%m-%d_%H-%M-%S)
ARCHIVO_BACKUP="/ruta/del/backup/backup_$FECHA.tar.gz"

# Crear el backup
tar -czf $ARCHIVO_BACKUP $DIRECTORIO

# Confirmación
echo "Backup de $DIRECTORIO creado en $ARCHIVO_BACKUP"


```

## Hacer el Script Ejecutable

```
chmod +x /ruta/a/tu/backup.sh

```

## Configurar Cron

### Abrir el archivo crontab para edición:

```
crontab -e

```

## Agregar una línea para ejecutar el script a la hora deseada:

La sintaxis de cron es minuto hora día-del-mes mes día-de-la-semana comando. Por ejemplo, para ejecutar el script todos los días a las 2:30 AM, agregarías la siguiente línea:

```
30 2 * * * /ruta/a/tu/backup.sh /ruta/del/directorio/a/resguardar

```

### Información de la configuración aplicada: 

1. 30: El minuto en que se ejecutará el trabajo (30).
2. 2: La hora en formato de 24 horas (2 AM).
3. *: Cada día del mes.
4. *: Cada mes.
5. *: Cada día de la semana.
6. /ruta/a/tu/backup.sh /ruta/del/directorio/a/resguardar: El comando a ejecutar, incluyendo el parámetro del directorio.

### Guardar con Ctrl+0 y salir con Ctrl+x

### Verificar que está bien configurado: 

```
crontab -l

```