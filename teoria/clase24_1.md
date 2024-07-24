# Examen Entrega 29/04/24

## Ejercicio 1: 
Dada la siguiente ip 172.30.0.0/22 indica todo lo que sepas de ella (3 puntos)

## Ejercicio 2: 
Dada la siguiente base de datos realiza el diagrama ER, explica todo lo que puedas de ella e inserta elementos en las tablas. (4 puntos)

```SQL
-- Crear la base de datos
CREATE DATABASE MantenimientoPiscinas;

-- Conectar a la base de datos
\c MantenimientoPiscinas;

-- Crear la tabla de Piscinas
CREATE TABLE Piscinas (
    id SERIAL PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL,
    ubicacion VARCHAR(255),
    capacidad FLOAT,
    fecha_construccion DATE
);

-- Crear la tabla de ProductosQuimicos
CREATE TABLE ProductosQuimicos (
    id SERIAL PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL,
    tipo VARCHAR(100),
    cantidad FLOAT,
    fecha_vencimiento DATE
);

-- Crear la tabla de Mantenimiento
CREATE TABLE Mantenimiento (
    id SERIAL PRIMARY KEY,
    fk_id_piscina INT,
    fk_id_producto INT,
    fk_id_empleado INT,
    fecha DATE,
    descripcion TEXT,
    costo FLOAT,
    FOREIGN KEY(id_piscina) REFERENCES Piscinas(id),
    FOREIGN KEY(fk_id_producto) REFERENCES ProductosQuimicos(id),
    FOREIGN KEY(fk_id_empleado) REFERENCES Empleados(id),
);

-- Crear la tabla de Empleados
CREATE TABLE Empleados (
    id SERIAL PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL,
    apellido VARCHAR(100) NOT NULL,
    cargo VARCHAR(100)
);

```

## Ejercicio 3: 
Muestra y explica cómo accedes a la vista de desarrollador, muestra un modelo y una de sus vistas relacionadas, indica todo lo que puedas explicar de esto. (3 puntos)
