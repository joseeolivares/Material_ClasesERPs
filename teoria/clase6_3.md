# Funciones y algunos comandos para procesos

## Funciones

En bash podemos declarar y usar funciones, esto son subprogramas que permiten asilar tareas.

La sintaxis es:

```sh
nombre_funcion() {
    # Código de la función
    # Puedes usar "$1", "$2", etc., para acceder a los parámetros
    parametro1="$1"
    parametro2="$2"
    # Resto del código de la función
}
```

- Ejemplo: Con parámetros, pueden o no tenerlos

```sh
#!/bin/bash

# Definir una función llamada "saludar" que toma dos parámetros
saludar() {
    nombre="$1"
    saludo="$2"
    echo "$saludo, $nombre!"
}

# Llamar a la función con argumentos
saludar "Juan" "Hola"
saludar "María" "Buenos días"

```

- Salida:

```
Hola, Juan!
Buenos días, María!

```

Disponemos en Ubuntu de muchos comandos que nos permiten interactuar con procesos, veamos algunos:

## &(Ampersand):

Permite ejecutar procesos en segundo plano y deja la terminal libre para continuar realizando otras tareas.

La ejecución se realizaría de la siguiente manera:

```
comando &
```

### Ejemplo:

- Ejecuta la calculadora en el entorno gráfico: para ello debes abrir la terminal y escribir el siguiente comando:

```
gnome-calculator
```

Esto abre la calculadora pero bloquea la terminal (no te permite ejecutar comandos hasta que se cierra)

- Ahora ejecuta la calculadora usando & al final y verás la diferencia y utilidad de esto.

## ps (Process Status):

Muestra información sobre los procesos en ejecución, incluidos su ID, estado, recursos utilizados y más. Puede mostrar una lista detallada o filtrarse para procesos específicos.

Utiliza el manual para saber más sobre ps.

## free

Muestra información sobre la memoria RAM y el swap en el sistema, incluyendo la cantidad de memoria utilizada, libre y en caché.

La información se muestra en bytes.

## top

Proporciona una vista en tiempo real de los procesos que consumen recursos en el sistema, incluyendo la CPU y la memoria.

## kill

Se utiliza para enviar señales a procesos, lo que permite detener o terminar procesos.
