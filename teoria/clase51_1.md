# Ejemplos de Introducción a la POO en Python

La Programación Orientada a Objetos es un paradigma de programación que utiliza "objetos" y sus interacciones para diseñar y programar aplicaciones. Los principales conceptos de POO son:

## Clases y Objetos:

- Clase: Es una plantilla para crear objetos (una especie de plano).
- Objeto: Es una instancia de una clase.

## Encapsulamiento:

Consiste en ocultar los detalles internos de un objeto y exponer solo lo necesario. Se logra mediante métodos y propiedades.

## Herencia:

Permite crear una nueva clase que reutiliza, extiende y modifica el comportamiento de una clase existente.

## Polimorfismo:

Permite usar una interfaz común para diferentes tipos de datos. Se refiere a la capacidad de un método para actuar de diferentes maneras según el objeto que la llame.

## Ejemplos

### Clases y objetos

```py
# Definición de una clase
class Persona:
    # Constructor de la clase
    def __init__(self, nombre, edad):
        self.nombre = nombre
        self.edad = edad
    
    # Método de la clase
    def saludar(self):
        print(f"Hola, mi nombre es {self.nombre} y tengo {self.edad} años.")

# Creación de un objeto
persona1 = Persona("Juan", 30)

# Llamada a un método del objeto
persona1.saludar()

```

### Encapsulamiento

```py
class CuentaBancaria:
    def __init__(self, titular, saldo):
        self.titular = titular
        self.__saldo = saldo  # Atributo privado
    
    def depositar(self, cantidad):
        self.__saldo += cantidad
    
    def retirar(self, cantidad):
        if cantidad <= self.__saldo:
            self.__saldo -= cantidad
        else:
            print("Saldo insuficiente")
    
    def obtener_saldo(self):
        return self.__saldo

# Crear un objeto de CuentaBancaria
cuenta = CuentaBancaria("Ana", 1000)
cuenta.depositar(500)
cuenta.retirar(200)
print(cuenta.obtener_saldo())  # Salida: 1300

```

### Herencia

```py
# Clase base
class Animal:
    def __init__(self, nombre):
        self.nombre = nombre
    
    def hacer_sonido(self):
        pass

# Clase derivada
class Perro(Animal):
    def hacer_sonido(self):
        print("Guau")

class Gato(Animal):
    def hacer_sonido(self):
        print("Miau")

# Crear objetos de las clases derivadas
perro = Perro("Rex")
gato = Gato("Whiskers")

perro.hacer_sonido()  # Salida: Guau
gato.hacer_sonido()   # Salida: Miau

```

### Polimorfismo

```py
class Ave:
    def volar(self):
        print("El ave vuela")

class Pinguino(Ave):
    def volar(self):
        print("El pingüino no puede volar")

# Función que demuestra el polimorfismo
def hacer_volar(ave):
    ave.volar()

# Crear objetos
ave = Ave()
pinguino = Pinguino()

# Llamada a la función con diferentes objetos
hacer_volar(ave)        # Salida: El ave vuela
hacer_volar(pinguino)   # Salida: El pingüino no puede volar

```

