# Base de Datos Relacionales
## Tarea 6 y 7
### Instrucciones

- Usar funciones de agregación para calcular en tu base de datos.
a) conteo de frecuencias o media
b) Mínimos o máximos
c) Cuantil cuyo resultado sea distinto a la media
d) Moda
e) Reporta hallazgos, dificultades, implementación de soluciones encontradas en línea, etc. 
- Haz al menos un ejemplo de cada una de estas consultas de estadísticos
- Revisa inconsistencias en tu base de datos
- Haz modificaciones o ajustes que faciliten la manipulación de tu base de datos usando lenguaje SQL
- Utiliza subconsultad para responder preguntas relevantes de tus datos
- Reporta tus hallazgos en un archivo MD o PDF claramente identificado en tu repositorio (puede ser en la tarea 6).

### **a). Conteo de frecuencias o media**
```postgresql
### Media de edad de los jóvenes
SELECT AVG(edad) AS media_edad_jovenes
FROM jovenes;
```

```postgresql
### Conteo de jóvenes por nivel educativo
SELECT nivel_educativo, COUNT(*) AS frecuencia
FROM jovenes
GROUP BY nivel_educativo;
```

### **b). Mínimos o máximos**
```postgresql
### Edad mínima y máxima entre los jóvenes
SELECT MIN(edad) AS edad_minima, MAX(edad) AS edad_maxima
FROM jovenes;
```

### **c). Cuantil cuyo resultado sea distinto a la media**
```postgresql
### Cuantil 50% (mediana) aproximada
SELECT edad
FROM (
  SELECT edad,
         ROW_NUMBER() OVER (ORDER BY edad) AS fila,
         COUNT(*) OVER () AS total
  FROM jovenes
) AS ordenados
WHERE fila = FLOOR((total + 1) / 2);

###Para comparar con la media
SELECT
  (SELECT AVG(edad) FROM jovenes) AS media,
  (SELECT edad
   FROM (
     SELECT edad,
            ROW_NUMBER() OVER (ORDER BY edad) AS fila,
            COUNT(*) OVER () AS total
     FROM jovenes
   ) AS ordenados
   WHERE fila = FLOOR((total + 1) / 2)
  ) AS mediana;
```

### **d). Moda**
```postgresql
### Moda de edad entre los jóvenes
SELECT edad
FROM jovenes
GROUP BY edad
ORDER BY COUNT(*) DESC
LIMIT 1;
```