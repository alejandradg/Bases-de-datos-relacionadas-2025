# Base de Datos Relacionales
## Tarea 4
### Instrucciones

- Crea tu base de datos y tablas correspondientes a partir de tus tareas de los modelos e-r y relacional.
- Incluye al menos 20 registros en tu base de datos
- Sube tu archivo de creación de base de datos a tu repositorio con un nombre claro en formato SQL (o equivalente)
- Tu archivo se ejecuta completamente y sin ningún error en su SGBD correspondiente.

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
(5, 'Casa rural', 'Adobe', FALSE, FALSE),
(6, 'Casa independiente', 'Block', TRUE, TRUE),
(7, 'Departamento', 'Concreto armado', TRUE, TRUE),
(8, 'Casa dúplex', 'Ladrillo rojo', FALSE, TRUE),
(9, 'Casa móvil', 'Metal y madera', TRUE, FALSE),
(10, 'Casa pequeña', 'Madera', FALSE, FALSE),
(11, 'Casa urbana', 'Block', TRUE, TRUE),
(12, 'Condominio', 'Concreto armado', TRUE, TRUE),
(13, 'Casa dúplex', 'Tabique', FALSE, TRUE),
(14, 'Casa improvisada', 'Cartón', TRUE, FALSE),
(15, 'Rancho', 'Adobe y palma', FALSE, FALSE),
(16, 'Villa', 'Concreto', TRUE, TRUE),
(17, 'Loft', 'Concreto ligero', TRUE, TRUE),
(18, 'Cabaña', 'Madera', FALSE, FALSE),
(19, 'Casa antigua', 'Piedra', TRUE, FALSE),
(20, 'Edificio multifamiliar', 'Concreto', TRUE, TRUE);

### Insertar registros en hogares
INSERT INTO hogares VALUES
(101, 1, 5, 'Nuclear', 'Alta participación'),
(102, 2, 3, 'Extendida', 'Media participación'),
(103, 3, 4, 'Nuclear', 'Baja participación'),
(104, 4, 2, 'Monoparental', 'Sin participación'),
(105, 5, 6, 'Extendida', 'Alta participación'),
(106, 6, 4, 'Nuclear', 'Media participación'),
(107, 7, 3, 'Nuclear', 'Alta participación'),
(108, 8, 5, 'Extendida', 'Baja participación'),
(109, 9, 2, 'Monoparental', 'Ninguna'),
(110, 10, 3, 'Nuclear', 'Alta participación'),
(111, 11, 6, 'Nuclear', 'Media participación'),
(112, 12, 4, 'Extendida', 'Baja participación'),
(113, 13, 5, 'Monoparental', 'Alta participación'),
(114, 14, 3, 'Nuclear', 'Media participación'),
(115, 15, 4, 'Extendida', 'Baja participación'),
(116, 16, 2, 'Monoparental', 'Ninguna'),
(117, 17, 3, 'Nuclear', 'Alta participación'),
(118, 18, 6, 'Nuclear', 'Media participación'),
(119, 19, 4, 'Extendida', 'Baja participación'),
(120, 20, 5, 'Monoparental', 'Alta participación');

### Insertar registros en jovenes
INSERT INTO jovenes VALUES
(201, 101, 17, 'Bachillerato', 'Estudiante', 'Club juvenil'),
(202, 102, 19, 'Universidad', 'Trabaja medio tiempo', 'Ninguna'),
(203, 103, 16, 'Secundaria', 'Estudiante', 'Equipo deportivo'),
(204, 104, 20, 'Universidad', 'Busca trabajo', 'Voluntariado'),
(205, 105, 18, 'Preparatoria', 'Trabaja', 'Ninguna'),
(206, 106, 17, 'Secundaria', 'Estudiante', 'Iglesia'),
(207, 107, 19, 'Universidad', 'Estudia y trabaja', 'Club juvenil'),
(208, 108, 18, 'Preparatoria', 'Busca trabajo', 'Ninguna'),
(209, 109, 17, 'Bachillerato', 'Estudiante', 'Voluntariado'),
(210, 110, 16, 'Secundaria', 'Estudiante', 'Ninguna'),
(211, 111, 18, 'Preparatoria', 'Trabaja', 'Deportes'),
(212, 112, 20, 'Universidad', 'Estudia y trabaja', 'Ninguna'),
(213, 113, 19, 'Universidad', 'Estudia', 'Grupo ambiental'),
(214, 114, 17, 'Bachillerato', 'Estudiante', 'Ninguna'),
(215, 115, 16, 'Secundaria', 'Estudiante', 'Música'),
(216, 116, 18, 'Preparatoria', 'Trabaja', 'Ninguna'),
(217, 117, 17, 'Bachillerato', 'Estudiante', 'Club de ciencia'),
(218, 118, 16, 'Secundaria', 'Estudiante', 'Voluntariado'),
(219, 119, 19, 'Universidad', 'Estudia', 'Iglesia'),
(220, 120, 18, 'Preparatoria', 'Busca trabajo', 'Ninguna');

### Insertar registros en demograficas
INSERT INTO demograficas VALUES
(301, 101, 'Padre', TRUE, 'Trabaja', TRUE, 'Secundaria'),
(302, 102, 'Madre', TRUE, 'Ama de casa', FALSE, 'Primaria'),
(303, 103, 'Hermano', FALSE, 'Estudiante', TRUE, 'Preparatoria'),
(304, 104, 'Tía', FALSE, 'Trabaja', FALSE, 'Secundaria'),
(305, 105, 'Abuela', TRUE, 'Jubilada', FALSE, 'Primaria'),
(306, 106, 'Padre', TRUE, 'Trabaja', TRUE, 'Universidad'),
(307, 107, 'Madre', TRUE, 'Ama de casa', FALSE, 'Primaria'),
(308, 108, 'Hermana', FALSE, 'Estudiante', FALSE, 'Preparatoria'),
(309, 109, 'Tío', TRUE, 'Trabaja', TRUE, 'Universidad'),
(310, 110, 'Primo', FALSE, 'Estudiante', TRUE, 'Secundaria'),
(311, 111, 'Padre', TRUE, 'Trabaja', TRUE, 'Secundaria'),
(312, 112, 'Madre', TRUE, 'Ama de casa', FALSE, 'Primaria'),
(313, 113, 'Hermano', FALSE, 'Estudiante', TRUE, 'Preparatoria'),
(314, 114, 'Tía', FALSE, 'Trabaja', FALSE, 'Secundaria'),
(315, 115, 'Abuela', TRUE, 'Jubilada', FALSE, 'Primaria'),
(316, 116, 'Padre', TRUE, 'Trabaja', TRUE, 'Universidad'),
(317, 117, 'Madre', TRUE, 'Ama de casa', FALSE, 'Primaria'),
(318, 118, 'Hermana', FALSE, 'Estudiante', FALSE, 'Preparatoria'),
(319, 119, 'Tío', TRUE, 'Trabaja', TRUE, 'Universidad'),
(320, 120, 'Primo', FALSE, 'Estudiante', TRUE, 'Secundaria');

```


#### Materiales de aprendizaje: 
En esta sección incluyo todos los materiales (videos, artículos y documentación) que consulté mientras trabajaba en esta tarea. Los mantengo como referencia para mi yo del futuro. 

**Aprendizaje: Cómo Descargar MySQL**
Code 503. (2024). Tutorial - Cómo instalar MySQL y MySQL Workbench 2024. [Video]. Youtube. https://youtu.be/EmQZt6o6-78?si=Sq1l-KgtkQ510V_w


**Aprendizaje: Cómo Descargar Visual Studio 2029x64 redistributable**

CholanaaduApps. (2024). Tutorial - My SQL installer requires visual studio 2019x64 redistributable. [Video]. Youtube. https://youtu.be/zYiY77cWXig?si=joa9d_huVfNHKK49
