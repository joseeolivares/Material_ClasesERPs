# Módulo con vista, seguridad y datos de prueba: 

## Paso 1: Vamos a trabajar con modulo1, creado ayer

## Paso 2: La estructura de carpteas va a ser la siguiente: 

```
modulo1/
├── __init__.py
├── __manifest__.py
├── models/
│   ├── __init__.py
│   └── tarea.py
├── security/
│   └── ir.model.access.csv
├── views/
│   └── tarea_views.xml
└── demo/
    └── demo.xml

```
## Paso 3: Modifica el manifest y déjalo con este contenido: 

```py
{

    'name': 'Modulo1',
    'version': '1.0',
    'category': 'Uncategorized',
    'summary': 'Gestión de Tareas',
    'description': """
        Módulo para la gestión de tareas.
    """,
    'author': 'Tu Nombre',
    'depends': ['base'],
    'data': [
        'security/ir.model.access.csv',
        'views/tarea_views.xml',
    ],
    'demo': [
        'demo/demo.xml',
    ],
    'installable': True,
    'application': True,

}

```

## Paso 4: Dentro de models crea tarea.py y ponle el siguiente contenido: 

```py
from odoo import models, fields

class Tarea(models.Model):

    _name = 'modulo1.tarea'

    _description = 'Tareas'

    nombre = fields.Char(string='Nombre', required=True)
    descripcion = fields.Text(string='Descripción')
    activa = fields.Boolean(string='Activa', default=True)

```

## Paso 5: El init de models debe importar tarea: 

```py
from . import tarea
```
## Paso 6: Crea una carpeta security dentro de la raíz

## Paso 7: Crea un fichero ir.model.access.csv dentro de security con el siguiente contenido: 

```csv
id,name,model_id:id,group_id:id,perm_read,perm_write,perm_create,perm_unlink
access_modulo1_tarea_user,access.modulo1.tarea.user,model_modulo1_tarea,,1,0,0,0

```

## Paso 8: Dentro de la carpeta views, elimina el fichero que hay y crea uno llamado tarea_views.xml con el siguiente contenido: 

```xml
<odoo>

    <!-- Vista de Árbol -->
    <record id="view_tree_modulo1_tarea" model="ir.ui.view">
        <field name="name">modulo1.tarea.tree</field>
        <field name="model">modulo1.tarea</field>
        <field name="arch" type="xml">
            <tree string="Tareas">
                <field name="nombre"/>
                <field name="activa"/>
            </tree>
        </field>
    </record>
    <!-- Vista de Formulario -->
    <record id="view_form_modulo1_tarea" model="ir.ui.view">
        <field name="name">modulo1.tarea.form</field>
        <field name="model">modulo1.tarea</field>
        <field name="arch" type="xml">
            <form string="Tarea">¡
                <sheet>
                    <group>
                        <field name="nombre"/>
                        <field name="descripcion"/>
                        <field name="activa"/>
                    </group>
                </sheet>
            </form>
        </field>
    </record>
    <!-- Acción -->
    <record id="action_modulo1_tarea" model="ir.actions.act_window">
        <field name="name">Tareas</field>
        <field name="res_model">modulo1.tarea</field>
        <field name="view_mode">tree,form</field>
    </record>
    <!-- Menú y Submenú -->
    <menuitem id="menu_modulo1_root" name="Modulo1"/>
    <menuitem id="menu_modulo1_tarea" name="Tareas" parent="menu_modulo1_root" sequence="1"/>
    <menuitem id="submenu_modulo1_tarea" name="Tareas" parent="menu_modulo1_tarea" action="action_modulo1_tarea"/>
</odoo>
```

## Paso 9: Crea la carpeta demo

## Paso 10: Dentro de demo crea el fichero demo.xml con el siguiente contenido: 

```xml
<odoo>
    <record id="demo_tarea_1" model="modulo1.tarea">
        <field name="nombre">Tarea de ejemplo 1</field>
        <field name="descripcion">Esta es una tarea de ejemplo</field>
        <field name="activa">True</field>
    </record>
    <record id="demo_tarea_2" model="modulo1.tarea">
        <field name="nombre">Tarea de ejemplo 2</field>
        <field name="descripcion">Esta es otra tarea de ejemplo</field>
        <field name="activa">False</field>
    </record>
</odoo>
```
## Paso 11: En modo desarrollador y tras reiniciar Odoo, desinstala modulo1 y vuelve a instalarlo.

## Paso 12: Comprueba que puedes ver tareas dentro de Odoo y de la BD

