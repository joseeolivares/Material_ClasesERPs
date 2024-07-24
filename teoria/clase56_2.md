# Ejercicio API REST

## Primera parte: Base de Datos

Crea una Base de Datos en PostgreSQL llamada Empresa, que tenga una tabla llamada empleados, en la que se puedan insertar empleados con el formato de los ejemplos con los que hemos trabajado.

Formato: 

```js
    {
        'id': 0,
        'nombre': 'Davinia',
        'apellidos': 'de la Rosa',
        'trabaja_desde': '5'
    }
```
El campo **trabaja_desde** es un entero que representa la antigüedad del empleado en la empresa en años.

## Segunda parte: Back-end

Realiza en Python una API REST que tenga las siguientes características (Endpoint/method/comportamiento): 

1. **/all (GET):** Devuelve todos los empleados.
2. **/all/id (GET):** Devuelve un empleado por id
3. **/insert (POST):** Inserta un empleado
4. **/delete (DELETE):** Borra un empleado
5. **/update/id/nombre (PUT):** Actualiza el nombre de un empleado localizado por id

Recuerda que todas las peticiones que se hagan, deben devolver un JSON

## Tercera parte: Front-end
Realiza en HTML, CSS y JS una web que se comporte del siguiente modo (usando al Back-end): 

1. En el home muestre en una tabla o lista la información de todos los empleados.
2. Por medio de un formulario, permita escribir un id y buscar a un empleado por id.
3. Por medio de un formulario, permita solicitar todos los datos de un empleado nuevo e insertarlo.
4. Por medio de un formulario, permita escribir un id y borrar al empleado con dicho id.
5. Por medio de un formulario, permita escribir un id y un nombre y actualice el nombre del empleado con dicho id.
 
