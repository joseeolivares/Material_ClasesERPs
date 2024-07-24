# Creación de un modelo en Odoo 16:

## Paso 1: Instala un módulo nuevo llamado modulo1.

## Paso 2: Dentro de la carpeta models crea un ficheros llamado models.py con el siguiente contenido: 

```py
from odoo import models, fields, api

class tarea(models.Model):

	_name = "modulo1.tarea"

	_description = "Modelo personalizado para tareas"

	nombre = fields.Char()

```

## Paso 3: Dentro de la carpeta models modifica el fichero __init__py y déjalo con el siguiente contenido: 

```py
from . import models

```

## Paso 4: Asegúrate que el __init__py del directorio raíz del módulo tiene este contenido: 

```py
from . import models

```

## Paso 4: Reinicia Odoo

## Paso 5: Entra en modo desarrollador

## Paso 6: Actualiza la lista de apliaciones

## Paso 7: Ve a Ajustes-> Técnico -> Modelos y busca tu nuevo modelo por su nombre (¿Está en la Base de Datos?)

## Ejercicio: Debes diseñar modelos para tu módulo final, por lo que debes pensar la temática del mismo y la estructura para poder realizar el diseño.

[DOCUMENTACION_MODELOS](https://www.odoo.com/documentation/16.0/es/developer/tutorials/getting_started/04_basicmodel.html)


