# Base de Datos Relacionales
## Tarea 8
### Instrucciones
- Crear vistas (View) sobre consultas significativas, recurrentes, etc. que incluyan:
a). Incluyan un join
b). Incluyam un left join
c). Incluyan un right join
d). Incluyan una subconsulta

- Investigar y crear al menos un disparador (Trigger) de inserción, actualización o eliminación
- Guarda tus consultas como archivo SQL en tu repositorio
- Explicar qué hace cada vista y disparador que utilizas y qué beneficios para tu BD tiene crearlos
- Elegir tema para proyecto integrador de aprendizaje

### JOIN
```postgresql
CREATE VIEW vista_jovenes_vivienda AS
SELECT 
  j.joven_id,
  j.edad,
  j.nivel_educativo,
  h.num_integrantes,
  v.tipo_vivienda,
  v.material_construccion
FROM jovenes j
JOIN hogares h ON j.hogares_id = h.hogares_id
JOIN vivienda v ON h.vivienda_id = v.vivienda_id;
```

### Left Join
```postgresql
CREATE VIEW vista_hogares_y_jovenes AS
SELECT 
  h.hogares_id,
  h.num_integrantes,
  j.joven_id,
  j.edad
FROM hogares h
LEFT JOIN jovenes j ON h.hogares_id = j.hogares_id;
```

### Right Join
```postgresql
CREATE VIEW vista_jovenes_con_hogar AS
SELECT 
  j.joven_id,
  j.edad,
  h.hogares_id,
  h.composicion_familiar
FROM hogares h
RIGHT JOIN jovenes j ON h.hogares_id = j.hogares_id;
```

### Subconsulta
```postgresql
CREATE VIEW vista_jovenes_en_hogares_grandes AS
SELECT 
  j.joven_id,
  j.edad,
  h.hogares_id,
  h.num_integrantes
FROM jovenes j
JOIN hogares h ON j.hogares_id = h.hogares_id
WHERE h.num_integrantes > (
  SELECT AVG(num_integrantes) FROM hogares
);

SELECT * FROM vista_jovenes_vivienda;
SELECT * FROM vista_hogares_y_jovenes;
```

### Triger de inserción
```postgresql
CREATE TABLE auditoria_jovenes (
  id INT AUTO_INCREMENT PRIMARY KEY,
  joven_id INT,
  hogares_id INT,
  fecha_insercion DATETIME DEFAULT CURRENT_TIMESTAMP
);

DELIMITER $$

CREATE TRIGGER trg_after_insert_jovenes
AFTER INSERT ON jovenes
FOR EACH ROW
BEGIN
  INSERT INTO auditoria_jovenes (joven_id, hogares_id)
  VALUES (NEW.joven_id, NEW.hogares_id);
END$$

DELIMITER ;
```

### Funcionalidad de cada aspecto:

**Trigger**: Cada vez que inserto un nuevo joven en la tabla jovenes, el trigger guardaría automáticamente su "joven_id y hogares_id" en la tabla "auditoria_jovenes" junto con la fecha y hora del cambio. Para tener un control.

**Join**: Une dos tablas basándose en una columna en común.

**Left Join**: regresa todos los registros de la tabla izquierda

**Right Join**: regresa todos los registros de la tabla derecha, aunque no haya coincidencia en la izquierda.

**Subconsulta**: Es una consulta dentro de una consulta.