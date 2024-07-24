# jobs, fg, watch, pgrep y pkill

## jobs

El comando jobs se utiliza para gestionar trabajos en segundo plano en un shell Unix, como Bash. Un trabajo es una tarea o proceso que se ejecuta en segundo plano o en primer plano en una terminal. Cuando ejecutas un programa en una terminal, ese programa se convierte en un trabajo que está asociado a esa terminal. Estos trabajos se numeran de forma secuencial, comenzando desde 1, y se pueden gestionar utilizando los comandos jobs, fg y bg.

```
jobs sin opciones => Muestra los "trabajos" en segundo plano si los hay

jobs -l => Muestra además el PID de los procesos
```

## Trabajos en segundo plano

Un trabajo o proceso en segundo plano es un proceso que se ejecuta en la terminal sin bloquear la línea de comandos. Puedes enviar un trabajo en segundo plano utilizando el carácter & al final de un comando. Por ejemplo, comando & ejecutará "comando" en segundo plano.

## fg (foreground)

Se utiliza para mover un trabajo en segundo plano al primer plano. Esto significa que el trabajo se vuelve interactivo y aparece en la terminal actual. Puedes especificar el trabajo por su número de trabajo.

Ejemplo:

```
fg %1
```

### Ejercicio: Ejecuta la calculadora en segundo plano, mira su información con jobs y tráela a primer plano con fg

## watch

Se utiliza para ejecutar un comando repetidamente a intervalos regulares y mostrar su salida en la terminal. Esto es útil para monitorizar cambios en la salida de un comando en tiempo real.

Ejemplo:

```
$ watch -n 2 date  # Muestra la fecha actual cada 2 segundos

```

## pgrep

Se utiliza para buscar procesos en ejecución que coinciden con un patrón y muestra sus identificadores de proceso (PID). Puedes buscar procesos por nombre o por otros criterios.

- pgrep nombre_proceso: Busca procesos por nombre exacto.

Ejemplo:

```
$ pgrep firefox  # Busca procesos cuyo nombre sea "firefox"
```

## pkill

Se utiliza para enviar señales a procesos que coinciden con un patrón y finalizar esos procesos. Por defecto, pkill envía la señal SIGTERM, que suele ser una señal de terminación "suave".

- pkill -signal nombre_proceso: Envía una señal específica a los procesos que coinciden con el nombre del proceso.
  Ejemplo:

```
$ pkill -TERM firefox # Envía la señal SIGTERM al proceso "firefox"
```
