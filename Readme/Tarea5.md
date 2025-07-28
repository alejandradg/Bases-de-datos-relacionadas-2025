# Base de Datos Relacionales
## Tarea 5 
### Instrucciones

- Agregar datos ficticios o de otras fuentes de manera automática (mediante funciones como las vistas en esta tarea).
- Reportar en menos de 5 minutos hallazgos, dificultades, recomendaciones o recursos que sean relavantes.
- Calificación anónima dada en promedio por otros compañeros y autoevaluación

```postgresql
### Insertar registros adicionales en vivienda
INSERT INTO vivienda VALUES
(6, 'Casa de interés social', 'Concreto y ladrillo', TRUE, TRUE),
(7, 'Departamento en unidad', 'Block', TRUE, TRUE),
(8, 'Casa antigua', 'Adobe y teja', FALSE, FALSE),
(9, 'Habitación rentada', 'Madera', FALSE, FALSE),
(10, 'Casa móvil', 'Metal', TRUE, FALSE);

### Insertar registros adicionales en hogares
INSERT INTO hogares VALUES
(106, 6, 4, 'Nuclear', 'Media participación'),
(107, 7, 5, 'Extendida', 'Alta participación'),
(108, 8, 3, 'Monoparental', 'Baja participación'),
(109, 9, 2, 'Nuclear', 'Sin participación'),
(110, 10, 6, 'Extendida', 'Alta participación');

### Insertar registros adicionales en jovenes
INSERT INTO jovenes VALUES
(206, 106, 15, 'Secundaria', 'Estudiante', 'Grupo cultural'),
(207, 107, 21, 'Universidad', 'Trabaja', 'Voluntariado'),
(208, 108, 17, 'Preparatoria', 'Busca trabajo', 'Ninguna'),
(209, 109, 18, 'Bachillerato', 'Estudiante', 'Equipo deportivo'),
(210, 110, 20, 'Universidad', 'Trabaja medio tiempo', 'Club juvenil');

### Insertar registros adicionales en demograficas
INSERT INTO demograficas VALUES
(306, 106, 'Padre', TRUE, 'Trabaja', TRUE, 'Secundaria'),
(307, 106, 'Madre', TRUE, 'Ama de casa', FALSE, 'Preparatoria'),
(308, 107, 'Hermano', FALSE, 'Estudiante', TRUE, 'Secundaria'),
(309, 109, 'Abuelo', TRUE, 'Jubilado', TRUE, 'Primaria'),
(310, 110, 'Tío', TRUE, 'Trabaja', TRUE, 'Preparatoria');
```

### Dificultades y hallazgos

- Falta de documentación: como los nombres de variables no son intuitivos (en la base su nombre es P_5, P_108, etc) y no hay un diccionario de datos, esto puede dificultar su comprensión y uso correcto.

- Inserción en orden incorrecto: si intentas insertar un joven antes de que exista su hogar (violando la FK), el código fallará.