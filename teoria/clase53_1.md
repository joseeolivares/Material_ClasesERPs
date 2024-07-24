# Ejemplo petición POST Python + HTML    

## index.html

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <form action="http://127.0.0.1:5000/insert" method="post">
        <label for="">Nombre: </label>
        <input type="text" name="nombre" value="">
        <input type="submit" value="Enviar">
    </form>
</body>
</html>

```

## script.py

```py
import flask
from flask import request, jsonify

app = flask.Flask(__name__)

app.config["DEBUG"] = True

employees = [
   {'id': 0,
	'nombre': 'Davinia',
	'apellidos': 'de la Rosa',
	'trabaja_desde': '5'},
   {'id': 1,
	'nombre': 'Maria',
	'apellidos': 'Ramirez',
	'trabaja_desde': '4'},
   {'id': 2,
	'nombre': 'Lucas',
	'apellidos': 'Ruiz',
	'trabaja_desde': '4'}
]
# Ruta por defecto
@app.route('/', methods=['GET'])
def home():
 return '''<h1>API REST</h1><p>Ejemplo de API REST 2</p>'''

# Ruta para obtener todos los empleados
@app.route('/all', methods=['GET'])
def api_all():
   return jsonify(employees)

@app.route('/insert', methods=['POST'])
def api_insert():
	 # Obtener el dato del formulario del atributo name del input
    nombre = request.form.get('nombre')
    # Crear un diccionario con los datos
    data = {'nombre': nombre}
    # Devolver los datos en formato JSON
    return jsonify(data)

app.run()

```