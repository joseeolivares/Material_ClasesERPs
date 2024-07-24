# Hacer copia de Base de Datos Postgre

Vamos a resolver el problema de poder hacer una copia de una BD Postgre de dos maneras diferentes:

## Primera forma:

Los pasos que vamos a seguir son los siguientes:

1. Accede a una MV en la que tengas instalado Odoo.

2. Crea un directorio en tu home, da permisos de lectura, escritura y ejecución para el usuario postgre pueda hacer cambios en él.

3. Accede a dicho directorio.

4. Haz login con el usuario postgre

5. Entra en psql y crea una BD con una sola tabla y alguna inserción desde psql, esta BD sólo la vamos a usar para realizar un export, por lo que no es importante ni la estructura, ni los datos.

6. Crea un usuario con permisos dentro de la BD para hacer tu copia:

```SQL
CREATE USER usuario WITH PASSWORD 'password';
GRANT ALL PRIVILEGES ON DATABASE bd TO usuario;
```

7. Ejecuta el siguiente comando, fuera de psql:

```
pg_dump -h EXTERNAL_HOSTNAME -U USERNAME -p PORT -d DATABASE_NAME -C > export.sql
```

8. Intercambia con un compañero exports y raliza la importación:

```
psql -h EXTERNAL_HOSTNAME -U USERNAME -p PORT -d DATABASE_NAME < export.sql
```

## Segunda forma:

Los pasos del 4 al 8 son los mismos.

Lo que varía es que debes dar permisos para ejecutar comandos con sudo al usuario postgre, ya que en caso contrario no dispones de permisos para guardar el fichero de export.

[MAS_INFORMACION](https://kinsta.com/es/docs/importar-y-exportar-base-de-datos-postgresql-con-linea-de-comandos/)
