# Ejercicio BD

### Realiza el Diagrama ER, la creación de la BD incluyendo una configuración que consideres lógica para los ON UPDATE y ON DELETE, inserts, prueba de funcionamiento de ON UPDATE y ON DELETE, a partir del siguiente enunciado: 

La liga de fútbol profesional, presidida por Don Ángel María Villar, ha decidido informatizar sus instalaciones creando una base de datos para guardar la información de los partidos
que se juegan en la liga.

Se desea guardar en primer lugar los datos de los jugadores. De cada jugador se quiere guardar el nombre, fecha de nacimiento y posición en la que juega (portero, defensa,
centrocampista...). Cada jugador tiene un código de jugador que lo identifica de manera única.

De cada uno de los equipos de la liga es necesario registrar el nombre del equipo, nombre del estadio en el que juega, el aforo que tiene, el año de fundación del equipo y la ciudad 
de la que es el equipo. Cada equipo también tiene un código que lo identifica de manera única. Un jugador solo puede pertenecer a un único equipo.

De cada partido que los equipos de la liga juegan hay que registrar la fecha en la que se juega el partido, los goles que ha metido el equipo de casa y los goles que ha metido el equipo de fuera. Cada partido tendrá un código numérico para identificar el partido.

También se quiere llevar un recuento de los goles que hay en cada partido. Se quiere almacenar el minuto en el que se realizar el gol y la descripción del gol. Un partido tiene
varios goles y un jugador puede meter varios goles en un partido.

Por último se quiere almacenar, en la base de datos, los datos de los presidentes de los equipos de fútbol (dni, nombre, apellidos, fecha de nacimiento, equipo del que es
presidente y año en el que fue elegido presidente). Un equipo de fútbol tan sólo puede tener un presidente, y una persona sólo puede ser presidente de un equipo de la liga.

### Además, debes incluir un trigger que realice una copia de seguirdad de la tabla que consideres y pruebas de funcionamiento en tu script.

### Por último, realiza al menos un SELECT que use JOIN y dos que no.