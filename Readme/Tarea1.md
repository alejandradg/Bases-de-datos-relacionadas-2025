# Base de Datos Relacionales
## Tarea 1
### Instrucciones
- Crear un repositorio público en Github.
- Compartir el repositorio en el Teams correspondiente (o Drive, mientras haya Teams).
- Describir una base de datos y sus relaciones de manera no estructurada (puede ser un párrafo, lista, esquema...) con la que trabajarás durante el tetramestre. Agrega el típo de dato que supones que tendrá cada uno de tus atributos. 
- Investigar diferentes SGBD, elegir alguno y describirlo. Citar adecuadamente. Plagio invalida tarea. 
- Subir esta descripción en un archivo markdown o PDF nombrado claramente (tarea 1 o algo por el estilo)

### Base de Datos estructurada

Según el INEGI (2014), la base de la Encuesta de Cohesión Social para la prevención de la violencia y delincuencia (ECOPRED) organiza la información en diferentes tablas y bases. La encuesta se divide en 4 bases independientes (demográficas, viviendas, información de jóvenes, y hogares). Esta organización permite analizar factores sociales, económicos y territoriales asociados con conductas delictivas y violentas de los jóvenes. Sin embargo, bases como (demográficas y viviendas) pueden ser utilizadas para responder preguntas de diferentes tópicos; ya que ambas bases son usadas en INEGI para encuestas no relacionadas. 

**1) Viviendas:**

Contiene información sobre las características físicas y del entorno de una vivienda. Dentro de ella se pueden encontrar datos como: 
- Tipo de vivienda.
- Material predominante de techo, muros y pisos.
- Servicios como agua, luz, drenaje, servicio de recolección de basura.
- Equipos del hogar (refrigerador, lavadora, computadora).
- Percepción de la vivienda (seguridad, acceso a servicios públicos).

**2) Jóvenes**

Contiene información sobre los jóvenes. Dentro de ella se pueden encontrar datos de: 
- Edad, sexo, nivel educativo
- Condición laboral y educativa (trabaja, busca trabajo, estudia).
- Participación en organizaciones
- Experiencia con violencia, delitos y consumo de sustancias.

**3) Hogares**

Esta categoría permite identificar condiciones del hogar. 
- Número de integrantes en el hogar.
- Composición familiar.
- Ingresos totales del hogar.
- Percepción de cohesión social familiar.
- Participación en comunidad.
- Opinión sobre los programas sociales.

**4) Demográficas**

Agrupa información general de los individuos que viven en el hogar: 
- Edad de los integrantes del hogar
- Sexo
- Parentesco con los jefes del hogar
- Estado civil
- Nivel de escolaridad
- Condición de actividad (trabajando, buscando trabajo, estudiante)

### Descripción SGBD

**¿Qué son las SGBD relacionales?**

Un sistema de gestión de datos relacional es cualquier software que te permita crear, gestionar, organizar y manipular bases de datos estructuradas en forma de tablas. Estas tablas pueden estar relacionadas entre sí por medio de relaciones pre-definidas. Para las SGBD, uno de los lenguajes más utilizados es SQL (Structured Query Language). 

**MySQL**

Dentro del ecosistema SQL, MySQL es un sistema de gestión de bases de datos relacional de código abierto que permite almacenar, organizar y administrar grandes volúmenes de información de forma eficiente. Con MySQL es posible crear tablas y columnas, así como establecer relaciones entre los datos, lo que facilita su estructuración y consulta en aplicaciones de todo tipo.


### Bibliografía
Instituto Nacional de Estadística y Geografía (INEGI). (2014). Encuesta de Cohesión Social para la Prevención de la Violencia y la Delincuencia 2014 (ECOPRED) [Base de datos]. INEGI. Recuperado de https://www.inegi.org.mx/programas/ecopred/2014/#microdatos

MySQL. (2025). My SQL Global Forum. Recuperado de https://www.mysql.com/


