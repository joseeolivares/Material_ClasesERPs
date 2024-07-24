# Ejercicios obligatorios

## 7

Investigación: ¿Cómo puedo ver los permisos que tiene un archivo o directorio?

## 8

Dados dos enteros almacenados en variables, crea un script en bash que permita mostra en la terminal el mayor.

## 9

Pasando un nombre de directorio por parámetro al script en bash, permite que se cree un directorio con dicho nombre en **/home**

## 10

Pasando un nombre de usuario y una contraseña por parámetros a un script (primero user y segundo pass), validar a un usuario (el user correcto y el pass correcto estarán en una variable)

## 11

Crea un script que funcione del siguiente modo:

1. Si el usuario pone como primer parámetro 1 y una ruta, nos muestra el ls de dicha ruta (tratándose de un directorio)

2. Si el usuario pone 2 y un nombre de fichero, nos muestra el cat del fichero

## 12

Usando bucles y un script en bash, que recibe como parámetro un número entre 1 y 5 (sólo son válidos el 1, 2, 3, 4 y 5), crea tantos ficheros como número indique el usuario usando como nombre el propio número.

**Ejemplo:**

```
# Un ejemplo
./ficheros.sh 2

Salida:
Se han creado los ficheros 1.txt y 2.txt (y debes comprobar que así es usando ls)
# Otro ejemplo
./ficheros.sh 7
Salida:
Numero incorrecto

```

## 13

Usando bucles y un script en bash, que recibe como parámetros dos números, muestra los números que hay dentro del intervalo indicado por el usuario, teniendo en cuenta el orden en el que los indica e incluyendo los extremos.

**Ejemplo:**

```
# Un ejemplo:
./intervalo.sh 2 7

Salida:
2
3
4
5
6
7

# Otro ejemplo:
./intervalo.sh 7 2

Salida:
7
6
5
4
3
2

```
