# Base de Datos Relacionales
## Tarea 3
### Instrucciones

- Instalen un SGBD
- Instalen DBeaver
- Crea la base de datos y tablas correspondientes a su base de datos
- Incluye al menos 5 registros en tu base de datos (en total)


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


#### Materiales de aprendizaje: 
En esta sección incluyo todos los materiales (videos, artículos y documentación) que consulté mientras trabajaba en esta tarea. Los mantengo como referencia para mi yo del futuro. 

**Aprendizaje: Cómo Descargar MySQL**
Code 503. (2024). Tutorial - Cómo instalar MySQL y MySQL Workbench 2024. [Video]. Youtube. https://youtu.be/EmQZt6o6-78?si=Sq1l-KgtkQ510V_w


**Aprendizaje: Cómo Descargar Visual Studio 2029x64 redistributable**

CholanaaduApps. (2024). Tutorial - My SQL installer requires visual studio 2019x64 redistributable. [Video]. Youtube. https://youtu.be/zYiY77cWXig?si=joa9d_huVfNHKK49
