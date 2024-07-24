# Pasos completos para exportar una BD PostgreSQL tras instalar Odoo

## 1 Haz login con root en tu Ubuntu Server y da permisos de sudo al usuario postgres

Entramos al fichero 
```
visudo
```

Añadimos los permisos así, tras el usuario root: 

```
postgres ALL=(ALL:ALL) ALL
```

## 2 Cambia el password a postgres (continuamos con root)

Te recomiendo poner el mismo que tienes para el root
```
passwd postgres
```

## 3 Entra con postgres en psql 

## 4 Cambia el pass dentro del servidor de BD al usuario postgres (así podremos usar sus permisos para hacer el dump)

```SQL
ALTER USER postgres WITH PASSWORD 'tu_nueva_contraseña';

```

## 5 Sal de psql, ve a / con el usuario postgres y crea un directorio copias 

Asegúrate de que postgres es el propietario de copias 
```
cd /
sudo mkdir copias
ls -las
``` 

Si no lo es, que no tendría por qué, cambia el propietario y el grupo: 

```
sudo chown postgres /copias
sudo chgrp postgres /copias
```

## 6 Vuelve a psql y crea tu BD, te dejo una de ejemplo:

```SQL 
CREATE DATABASE prueba;

\c prueba 

CREATE TABLE prueba(
    id SERIAL PRIMARY KEY,
    campo VARCHAR(100)
);

INSERT INTO prueba(campo) VALUES('Davinia');
INSERT INTO prueba(campo) VALUES('Pedro');

```

## 7 Realiza la copia del esquema de la BD (la estructura)

Vamos a usar postgres

```
sudo pg_dump -h localhost -U postgres -p 5432 -d prueba -C -s -F plain > export_schema.sql

```

## 8 Realiza una copia de los datos

```
sudo pg_dump -h localhost -U postgres -p 5432 -d prueba -a -F plain > export_data.sql

```

## 9 Fusiona los ficheros para tener un sólo dump con todo

```

cat export_schema.sql export_data.sql > export.sql

```

## 10 Entra en psql y borra la BD para poder volver a crearla desde tu export.sql

```
DROP DATABASE prueba;
```

## 11 Realiza el import dentro de psql

```
\i '/copias/export.sql'
```

## 12 Comprueba que la BD existe y mira los datos

```
\l

SELECT * FROM prueba;
```

