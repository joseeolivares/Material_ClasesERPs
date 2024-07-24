## Ejercicios

### 1:

A partir del siguiente enunciado se desea realiza el modelo entidad-relación.

“Una empresa vende productos a varios clientes. Se necesita conocer los datos personales de los clientes (nombre, apellidos, dni, dirección y fecha de nacimiento). Cada producto tiene un nombre y un código, así como un precio unitario. Un cliente puede comprar varios productos a la empresa, y un mismo producto puede ser comprado por varios clientes.

Los productos son suministrados por diferentes proveedores. Se debe tener en cuenta que un producto sólo puede ser suministrado por un proveedor, y que un proveedor puede suministrar diferentes productos. De cada proveedor se desea conocer el NIF, nombre y dirección”.

### 2:

A partir del siguiente enunciado se desea realizar el modelo entidad-relación.
“Se desea informatizar la gestión de una empresa de transportes que reparte paquetes por toda España. Los encargados de llevar los paquetes son los camioneros, de los que se quiere guardar el dni, nombre, teléfono, dirección, salario y población en la que vive.

De los paquetes transportados interesa conocer el código de paquete, descripción,destinatario y dirección del destinatario. Un camionero distribuye muchos paquetes, y un paquete sólo puede ser distribuido por un camionero.

De las provincias a las que llegan los paquetes interesa guardar el código de provincia y el nombre. Un paquete sólo puede llegar a una provincia. Sin embargo, a una provincia pueden llegar varios paquetes.

De los camiones que llevan los camioneros, interesa conocer la matrícula, modelo, tipo y potencia. Un camionero puede conducir diferentes camiones en fechas diferentes, y un camión puede ser conducido por varios camioneros”.

### 3:

A partir del siguiente enunciado diseñar el modelo entidad-relación.
“Se desea diseñar la base de datos de un Instituto. En la base de datos se desea guardar los datos de los profesores del Instituto (DNI, nombre, dirección y teléfono). Los profesores imparten módulos, y cada módulo tiene un código y un nombre. Cada alumno está matriculado en uno o varios módulos. De cada alumno se desea guardar el nº de expediente, nombre, apellidos y fecha de nacimiento. Los profesores pueden impartir varios módulos, pero un módulo sólo puede ser impartido por un profesor. Cada curso tiene un grupo de alumnos, uno de los cuales es el delegado del grupo”.

### 4:

A partir del siguiente supuesto diseñar el modelo entidad-relación:
“Se desea diseñar una base de datos para almacenar y gestionar la información
empleada por una empresa dedicada a la venta de automóviles, teniendo en cuenta los siguientes aspectos:

- La empresa dispone de una serie de coches para su venta. Se necesita conocer la matrícula, marca y modelo, el color y el precio de venta de cada coche.

- Los datos que interesa conocer de cada cliente son el NIF, nombre, dirección, ciudad y número de teléfono: además, los clientes se diferencian por un código interno de la empresa que se incrementa automáticamente cuando un cliente se da de alta en ella. Un cliente puede comprar tantos coches como desee a la empresa. Un coche determinado solo puede ser comprado por un único cliente.

- El concesionario también se encarga de llevar a cabo las revisiones que se realizan a cada coche. Cada revisión tiene asociado un código que se incrementa automáticamente por cada revisión que se haga. De cada revisión se desea saber si se ha hecho cambio de filtro, si se ha hecho cambio de aceite, si se ha hecho cambio de frenos u otros. Los coches pueden pasar varias revisiones en el concesionario”.

### 5:

Una base de datos para una pequeña empresa debe contener información acerca de clientes, artículos y
pedidos. Hasta el momento se registran los siguientes datos en documentos varios:

- Para cada cliente: Número de cliente (único), Direcciones de envío (varias por cliente), Saldo, Límite de
  crédito (depende del cliente, pero en ningún caso debe superar los 3.000.000 pts), Descuento.

- Para cada artículo: Número de artículo (único), Fábricas que lo distribuyen, Existencias de ese artículo
  en cada fábrica, Descripción del artículo.

- Para cada pedido: Cada pedido tiene una cabecera y el cuerpo del pedido. La cabecera está formada
  por el número de cliente, dirección de envío y fecha del pedido. El cuerpo del pedido son varias líneas, en
  cada línea se especifican el número del artículo pedido y la cantidad.

Además, se ha determinado que se debe almacenar la información de las fábricas. Sin embargo, dado el
uso de distribuidores, se usará: Número de la fábrica (único) y Teléfono de contacto. Y se desean ver
cuántos artículos (en total) provee la fábrica. También, por información estratégica, se podría incluir
información de fábricas alternativas respecto de las que ya fabrican artículos para esta empresa.
Nota: Una dirección se entenderá como Nº, Calle, Comuna y Ciudad. Una fecha incluye hora.
Se pide hacer el diagrama ER para la base de datos que represente esta información

### 6:

Diseñar un esquema E/R que recoja la organización de una base de datos para contener la información
sobre todas las carreteras del país, sabiendo que se deben cumplir las siguientes especificaciones:

- Las carreteras están divididas en varias categorías (locales, comerciales, regionales, nacionales,
  autovías, etc).

- Las carreteras se dividen en tramos. Un tramo siempre pertenece a una única carretera y no puede
  cambiar de carretera.

- Un tramo puede pasar por varias comunas, interesando conocer el Km de la carretera y la comuna
  donde empieza el tramo y en donde termina.

- Para los tramos que suponen principio o final de carretera, interesa saber si es que la carretera
  concluye físicamente o es que confluye en otra carretera. En este caso, interesa conocer con qué
  carretera confluye y en qué kilómetro, tramo y comuna.

### 7:

Obtener el diagrama E/R para un sistema de control de vuelos adaptado a las siguientes reglas de
gestión (indicar las entidades, interrelaciones, etc., que se deducen de cada una de las reglas):

a) De cada aeropuerto se conoce su código, nombre, ciudad y país.

b) En cada aeropuerto pueden tomar tierra diversos modelos de aviones (el modelo de un avión
determina su capacidad, es decir, el número de plazas.

c) En cada aeropuerto existe una colección de programas de vuelo. En cada programa de vuelo se indica
el número de vuelo, línea aérea y días de la semana en que existe dicho vuelo.

d) Cada programa de vuelo despega de un aeropuerto y aterriza en otro.

e) Los números de vuelo son únicos para todo el mundo.

f) En cada aeropuerto hay múltiples aterrizajes y despegues. Todos los aeropuertos contemplados están
en activo, es decir, tienen algún aterrizaje y algún despegue.

g) Cada vuelo realizado pertenece a un cierto programa de vuelo. Para cada vuelo se quiere conocer su
fecha, plazas vacías y el modelo de avión utilizado.

h) Algunos programas de vuelo incorporan escalas técnicas intermedias entre los aeropuertos de salida y
de llegada. Se entiende por escala técnica a un aterrizaje y despegue consecutivos sin altas ó bajas de
pasajeros.

i) De cada vuelo se quieren conocer las escalas técnicas ordenadas asignándole a cada una un número
de orden.

Por ejemplo, el programa de vuelo 555 de Iberia con vuelos los lunes y jueves despega de BarajasMadrid-España y aterriza en Caudell-Sydney-Australia teniendo las siguientes escalas técnicas: 1- LosPradiños-Sao Paulo-Brasil, 2-El Emperador-Santiago-Chile y 3-Saint Kitts-Auckland-Nueva Zelanda.

¿Que cambios se producirán en el caso anterior si en las escalas pudiesen bajar o subir pasajeros?
