# Pasos para configurar la rotación de logs

## Instalar logrotate:

```
sudo apt-get update
sudo apt-get install logrotate

```

## Crear o editar un archivo de configuración para tu log específico:

Los archivos de configuración de logrotate pueden encontrarse en **/etc/logrotate.conf** (archivo principal) o en el directorio **/etc/logrotate.d/** (archivos específicos para cada servicio).

## Configurar un archivo de rotación de logs:

Vamos a crear un archivo de configuración para un log de ejemplo. Supongamos que queremos rotar el log /var/log/mi_aplicacion.log.

Crea un archivo de configuración en **/etc/logrotate.d/mi_aplicacion**:

```
sudo nano /etc/logrotate.d/mi_aplicacion

```

Con el siguiente contenido: 

```
/var/log/mi_aplicacion.log {
    daily                # Rotar diariamente
    missingok            # No mostrar error si falta el archivo de log
    rotate 7             # Mantener 7 archivos de log antiguos
    compress             # Comprimir archivos de log antiguos
    delaycompress        # Comprimir en la próxima rotación
    notifempty           # No rotar si el archivo de log está vacío
    create 0640 root root # Crear un nuevo archivo de log con estos permisos
    postrotate
        # Comandos a ejecutar después de la rotación
        systemctl reload mi_aplicacion > /dev/null
    endscript
}

```

## Probar la configuración:

Para asegurarte de que la configuración es correcta, puedes ejecutar logrotate en modo de prueba:

```
sudo logrotate -d /etc/logrotate.d/mi_aplicacion

```

Para ejecutar la rotación manualmente (fuera del cron job):

```
sudo logrotate -f /etc/logrotate.d/mi_aplicacion
```

## Configuración: 

```
    /var/log/mi_aplicacion.log: Especifica el archivo de log que se va a rotar.

    daily: Rotar el log diariamente.

    missingok: No muestra error si el archivo de log no existe.

    rotate 7: Mantiene 7 copias antiguas del log.

    compress: Comprime los logs rotados.

    delaycompress: Retrasa la compresión hasta la próxima rotación.

    notifempty: No rota el archivo si está vacío.

    create 0640 root root: Crea un nuevo archivo de log con permisos 0640, propiedad de root.
    
    postrotate ... endscript: Comandos que se ejecutan después de la rotación. En este ejemplo, se recarga el servicio mi_aplicacion para que comience a escribir en el nuevo archivo de log.

```