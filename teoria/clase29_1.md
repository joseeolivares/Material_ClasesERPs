# Programar tareas con cron

Los pasos para realizar la programación de tareas con Cron son: 

## 1 Instalación, si no lo tienes: 

```
sudo apt-get update
sudo apt-get install cron
```

## 2 Ver estado del servicio: 

```
sudo service cron status
```

## 3 Iniciar si estaba parado el servicio: 

```
sudo service cron start
```

## 4 Editar el fichero de configuración (nos dará a elegir el editor):

```
crontab -e
```

## 5 Programar mi tarea 

Por ejemplo: 

```
* * * * * comando_a_ejecutar
```

Los cinco asteriscos representan (en orden) minutos, horas, días del mes, meses y días de la semana. Puedes usar un número específico, un rango de números separados por un guion o una lista de números separados por comas. 

Por ejemplo, **0 2 * * *** ejecutaría el comando a las 2:00 AM todos los días.

Más ejemplos: 


```
0 2 * * * /ruta/al/script.sh -> Todos los días a las 2 AM
*/10 * * * * comando_a_ejecutar -> Cada 10 minutos
5 20 * * * /ruta/al/script.sh -> Todos los días a las 20.05
0 19 * * 1 /ruta/al/script.sh -> Todos los lunes a las 19 (0 domingo, 1 lunes...)
0 12 1 * * /ruta/al/script.sh -> El primer día del mes a las 12

```

### Ojo: El script debe tener permisos de ejecución y no se debe hacer entrada/salida con él.
## 6 Ver las tareas 

```
crontab -l

```

## Ejercicios 

1. Ejecutar un script que realice una tarea recibiendo los datos por un fichero.

2. Localizar los logs de cron