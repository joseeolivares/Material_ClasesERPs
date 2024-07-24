# Logrotate

## 1: Instalación:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install logrotate

```

## 2: Configuración de ejemplo

La configuración principal de Logrotate se encuentra en el archivo /etc/logrotate.conf. Además, puede tener archivos de configuración adicionales en el directorio /etc/logrotate.d/. Aquí hay un ejemplo básico:

```
sudo nano /etc/logrotate.conf

```

- Estructura básica:

```
# Comentario

/ruta/a/tus/archivos/de/log {
    configuración1
    configuración2
    ...
}

```

- Comentario: Las líneas que comienzan con # son comentarios y no afectan la configuración. Son útiles para incluir notas o explicaciones.

- Ruta a tus archivos de log: Indica la ruta o patrón de archivos de registro que deseas gestionar. Puedes especificar un archivo específico o un patrón que coincida con varios archivos. Por ejemplo: /var/log/\*.log.

- Configuraciones: Son opciones que controlan el comportamiento de Logrotate para los archivos de registro especificados. Algunas configuraciones comunes incluyen:

1. daily: Rota los archivos diariamente.
2. weekly: Rota los archivos semanalmente.
3. rotate N: Mantiene N versiones antiguas del archivo.
4. compress: Comprime los archivos antiguos.
5. delaycompress: Retrasa la compresión del último archivo rotado.
6. missingok: No muestra un error si el archivo de registro no existe.
7. notifempty: No rota el archivo si está vacío.
8. create mode owner group: Crea un nuevo archivo con el modo, propietario y grupo especificados.

- Ejemplo:

```
# Rota los archivos diariamente, mantiene 7 versiones antiguas,
# comprime los archivos antiguos y cambia los permisos y propietario.
/var/log/mislogs/*.log {
    daily
    rotate 7
    missingok
    notifempty
    compress
    delaycompress
    create 0640 usuario grupo
}

```

## 3: Probar manualmente

```
sudo logrotate -vf /etc/logrotate.conf # verbose y force (-vf)

```
