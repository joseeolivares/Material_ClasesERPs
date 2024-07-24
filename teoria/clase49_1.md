# Ejercicio 

Realiza un CRUD en Python de la siguiente BD: 

“Una empresa vende productos a varios clientes. Se necesita conocer los datos personales de los clientes (nombre, apellidos, dni, dirección y fecha de nacimiento). Cada producto tiene un nombre y un código, así como un precio unitario. Un cliente puede comprar varios productos a la empresa, y un mismo producto puede ser comprado por varios clientes.

Los productos son suministrados por diferentes proveedores. Se debe tener en cuenta que un producto sólo puede ser suministrado por un proveedor, y que un proveedor puede suministrar diferentes productos. De cada proveedor se desea conocer el NIF, nombre y dirección”.

La creación de las tablas y todos los datos de las operaciones de inserción, actualización, borrado y búsqueda, se deben pedir al usuario.

## Código ayuda: 

```py
import psycopg2
def conectar():
    conexion = 0
    try:
        conexion = psycopg2.connect(database='python', user='postgres', password='postgres')
    except: 
        print('Error')
    return conexion
def opciones1():
    opcion = 0
    print('Elige una opcion:')
    print('1. Insertar en una tabla')
    print('2. Borrar en una tabla')
    print('3. Actualizar datos en una tabla')
    print('4. Buscar en una tabla')
    print('5. Salir')
    opcion = int(input('')) 
    return opcion

def opciones2():
    opcion = 0
    print('Elige una tabla:')
    print('1. Clientes')
    print('2. Productos')
    print('3. Proveedores')
    print('4. Compras')
    print('5. Salir')
    opcion = int(input('')) 
    return opcion

def menu():
    opcion = 0
    opcion2 = 0
    while opcion != 5:
        opcion = opciones1()
        if opcion != 5:
            opcion2 = opciones2()
        if opcion == 1:
            if opcion2 == 1:
                print('Insert en Clientes') 
            if opcion2 == 2:
                print('Insert en Productos') 
            if opcion2 == 3:
                print('Insert en Proveedores') 
            if opcion2 == 4:
                print('Insert en Compras') 
        if opcion == 2:
            if opcion2 == 1:
                print('Borrar en Clientes') 
            if opcion2 == 2:
                print('Borrar en Productos') 
            if opcion2 == 3:
                print('Borrar en Proveedores') 
            if opcion2 == 4:
                print('Borrar en Compras') 
        if opcion == 3:
            if opcion2 == 1:
                print('Actualizar Clientes') 
            if opcion2 == 2:
                print('Actualizar Productos') 
            if opcion2 == 3:
                print('Actualizar Proveedores') 
            if opcion2 == 4:
                print('Actualizar Compras')
        if opcion == 4:
            if opcion2 == 1:
                print('Buscar en Clientes') 
            if opcion2 == 2:
                print('Buscar en Productos') 
            if opcion2 == 3:
                print('Buscar en Proveedores') 
            if opcion2 == 4:
                print('Buscar en Compras')
    
conexion = conectar()
menu()
```