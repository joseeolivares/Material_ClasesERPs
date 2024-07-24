# Ejercicios

## 21

Script para ejecutar procesos en segundo plano y mostrar información de los procesos en ejecución

Crea un script Bash llamado background_processes.sh que realice lo siguiente:

Ejecuta tres comandos diferentes en segundo plano utilizando &.
Muestra el ID de proceso (PID) y el nombre de cada proceso que se está ejecutando en segundo plano.
Espera a que los procesos finalicen.
Utiliza el comando ps para listar los procesos en ejecución y extraer información relevante.
Utiliza el comando kill para terminar todos los procesos ejecutados en segundo plano.

### Solución

```sh
#!/bin/bash

# Ejecuta tres comandos diferentes en segundo plano
command1() {
    sleep 5
}
command2() {
    sleep 10
}
command3() {
    sleep 8
}

command1 &
pid1=$!

command2 &
pid2=$!

command3 &
pid3=$!

echo "Procesos en segundo plano en ejecución:"
echo "PID   Comando"
echo "$pid1   command1"
echo "$pid2   command2"
echo "$pid3   command3"

# Espera a que los procesos finalicen
wait $pid1
wait $pid2
wait $pid3

# Utiliza el comando ps para listar los procesos en ejecución y extraer información relevante
echo "Procesos en ejecución después de la ejecución en segundo plano:"
ps aux | grep -E 'command1|command2|command3'

# Utiliza el comando kill para terminar todos los procesos ejecutados en segundo plano
kill $pid1 $pid2 $pid3

echo "Procesos terminados."

```

### Explicación

1. Definimos tres funciones llamadas command1, command2 y command3, que simplemente esperan durante un número específico de segundos utilizando el comando sleep.

2. Luego, ejecutamos cada una de estas funciones en segundo plano utilizando & y guardamos los PIDs resultantes en las variables pid1, pid2 y pid3, usando la variable $!

3. Mostramos información sobre los procesos en segundo plano, incluyendo sus PIDs y nombres.

4. Utilizamos el comando wait para esperar a que los procesos en segundo plano finalicen.

5. Después de esperar a que finalicen, utilizamos el comando ps para listar todos los procesos en ejecución y filtramos la información relacionada con los nombres de los comandos.

6. Finalmente, utilizamos el comando kill para terminar todos los procesos en segundo plano, especificando sus PIDs.

## 22

Script para ejecutar y controlar procesos en segundo plano

Crea un script Bash llamado control_background_processes.sh que realice lo siguiente:

- Ejecuta un proceso en segundo plano utilizando &.
- Muestra el PID del proceso en ejecución.
- Espera a que el usuario presione una tecla.
- Utiliza el comando kill para detener el proceso en segundo plano con el PID proporcionado.

## 23

Script para ejecutar procesos concurrentes en segundo plano

Crea un script Bash llamado concurrent_background_processes.sh que realice lo siguiente:

- Ejecuta cinco comandos diferentes en segundo plano utilizando &.
- Muestra el PID de cada proceso en ejecución.
- Espera a que todos los procesos finalicen.
- Utiliza el comando ps para listar y mostrar los procesos en ejecución.
- Utiliza el comando kill para detener un proceso específico en segundo plano con el PID proporcionado por el usuario.
