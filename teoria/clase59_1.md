# Ejemplos modelos Odoo con FKs

## 1:1 Usuarios-Contraseñas

### usuario.py
```py
from odoo import models, fields

class Usuario(models.Model):
    _name = 'modulo1.usuario'
    _description = 'Usuarios'

    nombre = fields.Char(string='Nombre', required=True)
    contrasena_id = fields.Many2one('modulo1.contrasena', string='Contraseña', ondelete='set null')

```

### contrasena.py
```py
from odoo import models, fields

class Contrasena(models.Model):
    _name = 'modulo1.contrasena'
    _description = 'Contraseñas'

    clave = fields.Char(string='Clave', required=True)
    usuario_id = fields.Many2one('modulo1.usuario', string='Usuario', ondelete='cascade', required=True)

```

### init.py de models

```py
from . import usuario
from . import contrasena

```

## 1:N Clientes-Productos

### cliente.py

```py
from odoo import models, fields

class Cliente(models.Model):
    _name = 'modulo1.cliente'
    _description = 'Clientes'

    nombre = fields.Char(string='Nombre', required=True)
    producto_ids = fields.One2many('modulo1.producto', 'cliente_id', string='Productos')
```

### producto.py

```py
from odoo import models, fields

class Producto(models.Model):
    _name = 'modulo1.producto'
    _description = 'Productos'

    nombre = fields.Char(string='Nombre', required=True)
    precio = fields.Float(string='Precio')
    cliente_id = fields.Many2one('modulo1.cliente', string='Cliente', ondelete='cascade')
```

### init.py de models

```py
from . import cliente
from . import producto
```

## N:M Productos-Proveedores

### producto.py

```py
from odoo import models, fields

class Producto(models.Model):
    _name = 'modulo1.producto'
    _description = 'Productos'

    nombre = fields.Char(string='Nombre', required=True)
    precio = fields.Float(string='Precio')
    proveedor_ids = fields.Many2many('modulo1.proveedor', string='Proveedores')

```

### proveedor.py

```py
from odoo import models, fields

class Proveedor(models.Model):
    _name = 'modulo1.proveedor'
    _description = 'Proveedores'

    nombre = fields.Char(string='Nombre', required=True)
    producto_ids = fields.Many2many('modulo1.producto', string='Productos')
```

### init.py de models

```py
from . import producto
from . import proveedor
```