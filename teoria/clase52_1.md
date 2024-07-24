# Primer ejemplo API REST

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
 return '''<h1>API REST</h1>
<p>Ejemplo de API REST</p>'''

# Routa para obtener todos los empleados
@app.route('/api/v1/resources/employees/all', methods=['GET'])
def api_all():
   return jsonify(employees)

app.run()

```