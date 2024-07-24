# Introducción a Python

En esta primera clase vamos a usar este intérprete online: 
[INTERPRETE](https://www.programiz.com/python-programming/online-compiler/) 

Veamos ejemplos con estructuras de control de flujo simples y estructuras de datos: 

```py
# If
x = 10
if x > 5:
    print("x es mayor que 5")
else:
    print("x es menor o igual a 5")

# Switch
y = 2
if y == 1:
    print("y es 1")
elif y == 2:
    print("y es 2")
elif y == 3:
    print("y es 3")
else:
    print("y no es 1, 2, ni 3")

# for 
for i in range(5):
    print(f"Iteración {i}")

# while
z = 0
while z < 5:
    print(f"z es {z}")
    z += 1

# listas
lista = [1, 2, 3, 4, 5]
if 3 in lista:
    print("3 está en la lista")
else:
    print("3 no está en la lista")

for elemento in lista:
    print(f"Elemento: {elemento}")

index = 0
while index < len(lista):
    print(f"Elemento en índice {index}: {lista[index]}")
    index += 1

# tuplas
tupla = (1, 2, 3, 4, 5)
if 4 in tupla:
    print("4 está en la tupla")
else:
    print("4 no está en la tupla")

for elemento in tupla:
    print(f"Elemento: {elemento}")

index = 0
while index < len(tupla):
    print(f"Elemento en índice {index}: {tupla[index]}")
    index += 1

# diccionarios
diccionario = {'a': 1, 'b': 2, 'c': 3}
if 'b' in diccionario:
    print("La clave 'b' está en el diccionario")
else:
    print("La clave 'b' no está en el diccionario")

for clave, valor in diccionario.items():
    print(f"Clave: {clave}, Valor: {valor}")

keys = list(diccionario.keys())
index = 0
while index < len(keys):
    key = keys[index]
    print(f"Clave: {key}, Valor: {diccionario[key]}")
    index += 1

```

[DOCUMENTACION_PYTHON](https://docs.python.org/es/3/contents.html)

[ESTRUCTURAS_CONTROL](https://docs.python.org/es/3/tutorial/controlflow.html)

[ESTRUCTURAS_DATOS](https://docs.python.org/es/3/tutorial/datastructures.html)

[EJERCICIOS](https://aprendeconalf.es/docencia/python/ejercicios/)
