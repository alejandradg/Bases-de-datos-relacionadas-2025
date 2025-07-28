```postgresql

### Crear base de datos y usarla
CREATE DATABASE IF NOT EXISTS ecopred;
USE ecopred;

### Eliminar tablas si ya existen
DROP TABLE IF EXISTS demograficas, jovenes, hogares, vivienda;

### Crear tabla vivienda
CREATE TABLE vivienda (
  vivienda_id INT PRIMARY KEY,
  tipo_vivienda VARCHAR(100),
  material_construccion VARCHAR(100),
  servicios BOOLEAN,
  equipos BOOLEAN
);

### Crear tabla hogares
CREATE TABLE hogares (
  hogares_id INT PRIMARY KEY,
  vivienda_id INT UNIQUE,
  num_integrantes INT,
  composicion_familiar VARCHAR(100),
  participacion_comunidad VARCHAR(100),
  FOREIGN KEY (vivienda_id) REFERENCES vivienda(vivienda_id)
);

### Crear tabla jovenes
CREATE TABLE jovenes (
  joven_id INT PRIMARY KEY,
  hogares_id INT,
  edad INT,
  nivel_educativo VARCHAR(100),
  condicion_laboral_edu VARCHAR(100),
  participacion_social VARCHAR(100),
  FOREIGN KEY (hogares_id) REFERENCES hogares(hogares_id)
);

### Crear tabla demograficas
CREATE TABLE demograficas (
  integrante_id INT PRIMARY KEY,
  hogares_id INT,
  parentesco_jefe VARCHAR(100),
  estado_civil BOOLEAN,
  condicion_actividad VARCHAR(100),
  sexo BOOLEAN,
  nivel_escolaridad VARCHAR(100),
  FOREIGN KEY (hogares_id) REFERENCES hogares(hogares_id)
);

### Insertar registros en vivienda
INSERT INTO vivienda VALUES
(1, 'Casa independiente', 'Block y concreto', TRUE, TRUE),
(2, 'Departamento', 'Concreto armado', TRUE, FALSE),
(3, 'Casa dúplex', 'Ladrillo', FALSE, TRUE),
(4, 'Cuarto en vecindad', 'Madera y lámina', TRUE, FALSE),
(5, 'Casa rural', 'Adobe', FALSE, FALSE);

### Insertar registros en hogares
INSERT INTO hogares VALUES
(101, 1, 5, 'Nuclear', 'Alta participación'),
(102, 2, 3, 'Extendida', 'Media participación'),
(103, 3, 4, 'Nuclear', 'Baja participación'),
(104, 4, 2, 'Monoparental', 'Sin participación'),
(105, 5, 6, 'Extendida', 'Alta participación');

### Insertar registros en jovenes
INSERT INTO jovenes VALUES
(201, 101, 17, 'Bachillerato', 'Estudiante', 'Club juvenil'),
(202, 101, 19, 'Universidad', 'Trabaja medio tiempo', 'Ninguna'),
(203, 102, 16, 'Secundaria', 'Estudiante', 'Equipo deportivo'),
(204, 104, 20, 'Universidad', 'Busca trabajo', 'Voluntariado'),
(205, 105, 18, 'Preparatoria', 'Trabaja', 'Ninguna');

### Insertar registros en demograficas
INSERT INTO demograficas VALUES
(301, 101, 'Padre', TRUE, 'Trabaja', TRUE, 'Secundaria'),
(302, 101, 'Madre', TRUE, 'Ama de casa', FALSE, 'Primaria'),
(303, 102, 'Hermano', FALSE, 'Estudiante', TRUE, 'Preparatoria'),
(304, 104, 'Tía', FALSE, 'Trabaja', FALSE, 'Secundaria'),
(305, 105, 'Abuela', TRUE, 'Jubilada', FALSE, 'Primaria');
```