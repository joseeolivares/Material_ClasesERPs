# Ejemplo módulo 2 modelos N:M y datos de demo

## Estructura del módulo

```
clientes_productos/
├── __init__.py
├── __manifest__.py
├── models/
│   ├── __init__.py
│   └── cliente.py
│   └── producto.py
├── security/
│   └── ir.model.access.csv
├── views/
│   └── cliente_views.xml
│   └── producto_views.xml
└── data/
    └── demo_data.xml
```

## clientes_productos/__manifest__.py

```py

{
    'name': 'Gestión de Clientes y Productos',
    'version': '1.0',
    'category': 'Uncategorized',
    'summary': 'Módulo de ejemplo para la gestión de clientes y productos',
    'description': """
        Módulo de ejemplo que permite la gestión de clientes y productos con una relación N:M.
    """,
    'author': 'Tu Nombre',
    'depends': ['base'],
    'data': [
        'security/ir.model.access.csv',
        'views/cliente_views.xml',
        'views/producto_views.xml',
        'data/demo_data.xml',
    ],
    'demo': [
        'data/demo_data.xml',
    ],
    'installable': True,
    'application': True,
}

```

## clientes_productos/__init__.py

```py
from . import models
```

## clientes_productos/models/__init__.py

```py
from . import cliente
from . import producto
```

## clientes_productos/models/cliente.py

```py
from odoo import models, fields

class Cliente(models.Model):
    _name = 'clientes_productos.cliente'
    _description = 'Cliente'

    nombre = fields.Char(string='Nombre', required=True)
    producto_ids = fields.Many2many('clientes_productos.producto', string='Productos')

```

## clientes_productos/models/producto.py

```py
from odoo import models, fields

class Producto(models.Model):
    _name = 'clientes_productos.producto'
    _description = 'Producto'

    nombre = fields.Char(string='Nombre', required=True)
    cliente_ids = fields.Many2many('clientes_productos.cliente', string='Clientes')

```

## clientes_productos/security/ir.model.access.csv

```csv
id,name,model_id:id,group_id:id,perm_read,perm_write,perm_create,perm_unlink
access_clientes_productos_cliente,access.clientes_productos.cliente,model_clientes_productos_cliente,,1,1,1,1
access_clientes_productos_producto,access.clientes_productos.producto,model_clientes_productos_producto,,1,1,1,1
```

## clientes_productos/views/cliente_views.xml

```xml
<odoo>
    <!-- Vista de Árbol para Clientes -->
    <record id="view_tree_clientes_productos_cliente" model="ir.ui.view">
        <field name="name">clientes_productos.cliente.tree</field>
        <field name="model">clientes_productos.cliente</field>
        <field name="arch" type="xml">
            <tree string="Clientes">
                <field name="nombre"/>
            </tree>
        </field>
    </record>

    <!-- Vista de Formulario para Clientes -->
    <record id="view_form_clientes_productos_cliente" model="ir.ui.view">
        <field name="name">clientes_productos.cliente.form</field>
        <field name="model">clientes_productos.cliente</field>
        <field name="arch" type="xml">
            <form string="Cliente">
                <sheet>
                    <group>
                        <field name="nombre"/>
                        <field name="producto_ids" widget="many2many_tags"/>
                    </group>
                </sheet>
            </form>
        </field>
    </record>

    <!-- Acción para Clientes -->
    <record id="action_clientes_productos_cliente" model="ir.actions.act_window">
        <field name="name">Clientes</field>
        <field name="res_model">clientes_productos.cliente</field>
        <field name="view_mode">tree,form</field>
    </record>

    <!-- Menú para Clientes -->
    <menuitem id="menu_clientes_productos_root" name="Gestión de Clientes y Productos"/>
    <menuitem id="menu_clientes_productos_cliente" name="Clientes" parent="menu_clientes_productos_root" action="action_clientes_productos_cliente"/>
</odoo>

```

## clientes_productos/views/producto_views.xml

```xml

<odoo>
    <!-- Vista de Árbol para Productos -->
    <record id="view_tree_clientes_productos_producto" model="ir.ui.view">
        <field name="name">clientes_productos.producto.tree</field>
        <field name="model">clientes_productos.producto</field>
        <field name="arch" type="xml">
            <tree string="Productos">
                <field name="nombre"/>
            </tree>
        </field>
    </record>

    <!-- Vista de Formulario para Productos -->
    <record id="view_form_clientes_productos_producto" model="ir.ui.view">
        <field name="name">clientes_productos.producto.form</field>
        <field name="model">clientes_productos.producto</field>
        <field name="arch" type="xml">
            <form string="Producto">
                <sheet>
                    <group>
                        <field name="nombre"/>
                        <field name="cliente_ids" widget="many2many_tags"/>
                    </group>
                </sheet>
            </form>
        </field>
    </record>

    <!-- Acción para Productos -->
    <record id="action_clientes_productos_producto" model="ir.actions.act_window">
        <field name="name">Productos</field>
        <field name="res_model">clientes_productos.producto</field>
        <field name="view_mode">tree,form</field>
    </record>

    <!-- Menú para Productos -->
    <menuitem id="menu_clientes_productos_producto" name="Productos" parent="menu_clientes_productos_root" action="action_clientes_productos_producto"/>
</odoo>

```

## clientes_productos/data/demo_data.xml

```xml
<!-- clientes_productos/data/demo_data.xml -->
<odoo>
    <!-- Datos de demostración para Clientes -->
    <record id="cliente_demo_1" model="clientes_productos.cliente">
        <field name="nombre">Cliente 1</field>
    </record>

    <record id="cliente_demo_2" model="clientes_productos.cliente">
        <field name="nombre">Cliente 2</field>
    </record>

    <!-- Datos de demostración para Productos -->
    <record id="producto_demo_1" model="clientes_productos.producto">
        <field name="nombre">Producto 1</field>
    </record>

    <record id="producto_demo_2" model="clientes_productos.producto">
        <field name="nombre">Producto 2</field>
    </record>

    <!-- Relación N:M entre Clientes y Productos -->
    <record id="cliente_producto_rel_1" model="clientes_productos.cliente">
        <field name="nombre">Cliente 1</field>
        <field name="producto_ids" eval="[(6, 0, [ref('producto_demo_1'), ref('producto_demo_2')])]"/>
    </record>

    <record id="cliente_producto_rel_2" model="clientes_productos.cliente">
        <field name="nombre">Cliente 2</field>
        <field name="producto_ids" eval="[(6, 0, [ref('producto_demo_1')])]"/>
    </record>
</odoo>

```