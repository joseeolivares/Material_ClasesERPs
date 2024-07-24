# Ejemplo Módulo CRUD Odoo 16

## Estructura del módulo: 

```
tareas/
├── __init__.py
├── __manifest__.py
├── models/
│   ├── __init__.py
│   └── tarea.py
├── security/
│   └── ir.model.access.csv
└── views/
    └── tarea_views.xml

```
perm_read,perm_write,perm_create,perm_unlink
## init.py del raíz

```py
# tareas/__init__.py
from . import models

```

## init.py models

```py
# tareas/models/__init__.py
from . import tarea

```

## tarea.py models

```py
# tareas/models/tarea.py
from odoo import models, fields

class Tarea(models.Model):
    _name = 'tareas.tarea'
    _description = 'Modelo para gestionar tareas'

    titulo = fields.Char(string='Título', required=True)

```

## ir.model.access.csv security

```csv
id,name,model_id:id,group_id:id,
access_tareas_tarea_user,access.tareas.tarea.user,model_tareas_tarea,,1,1,1,1

```

### perm_create está establecido en 1, lo que permite la creación de registros para todos los usuarios (ya que group_id:id está vacío).

## tarea.views.xml views

```xml
<!-- tareas/views/tarea_views.xml -->
<odoo>
    <!-- Vista de Árbol para Tareas -->
    <record id="view_tree_tareas_tarea" model="ir.ui.view">
        <field name="name">tareas.tarea.tree</field>
        <field name="model">tareas.tarea</field>
        <field name="arch" type="xml">
            <tree string="Tareas">
                <field name="titulo"/>
            </tree>
        </field>
    </record>

    <!-- Vista de Formulario para Tareas -->
    <record id="view_form_tareas_tarea" model="ir.ui.view">
        <field name="name">tareas.tarea.form</field>
        <field name="model">tareas.tarea</field>
        <field name="arch" type="xml">
            <form string="Tarea">
                <sheet>
                    <group>
                        <field name="titulo"/>
                    </group>
                </sheet>
            </form>
        </field>
    </record>

    <!-- Acción para Tareas -->
    <record id="action_tareas_tarea" model="ir.actions.act_window">
        <field name="name">Tareas</field>
        <field name="res_model">tareas.tarea</field>
        <field name="view_mode">tree,form</field>
    </record>

    <!-- Menú para Tareas -->
    <menuitem id="menu_tareas_root" name="Gestión de Tareas"/>
    <menuitem id="menu_tareas_tarea" name="Tareas" parent="menu_tareas_root" action="action_tareas_tarea"/>
</odoo>

```

## manifest.py

```py

# tareas/__manifest__.py
{
    'name': 'Gestión de Tareas',
    'version': '1.0',
    'category': 'Uncategorized',
    'summary': 'Módulo de ejemplo para la gestión de tareas',
    'description': """
        Módulo de ejemplo que permite la gestión de tareas con operaciones CRUD.
    """,
    'author': 'Tu Nombre',
    'depends': ['base'],
    'data': [
        'security/ir.model.access.csv',
        'views/tarea_views.xml',
    ],
    'installable': True,
    'application': True,
}

```