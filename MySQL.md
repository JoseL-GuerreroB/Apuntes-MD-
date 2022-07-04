# MySQL
---

## Conocimientos basicos
MySQL es un sistema de gestion de base de datos realacionales, escritoel cual utiliza el lenguaje sql.

### iniciar servidor y cerrar servidor
Escribe tu contraseña del usuario **root**
```sql
Enter password: *************
```
cerrar
```sql
exit
```

### Creación de variables
```sql
SET @curso = "Base de datos", @gestor = "mysql";
SET @curso = "Base de datos";
SET @gestor = "mysql";
```
### Obtener datos del servidor
```sql
SELECT @curso, @gestor;
```
obtenemos:

|@curso       |@gestor|
|-------------|-------|
|Base de datos|mysql  |

### Crear Base de datos
```sql
CREATE DATABASE escuela;
```
### Mostrar todas las bases de datos existentes
```sql
SHOW DATABASES;
```
### Eliminar base de datos
```sql
DROP DATABASE escuela;
```
### Usar base de datos
```sql
USE escuela;
```
### Crear una tabla
```sql
CREATE TABLE alumnos(
  alumno_id INT,
  numbre VARCHAR(50),
  apellido VARCHAR(50),
  genero CHAR(1),
  fecha_nacimiento DATE,
  pais_origen VARCHAR(40)
);
```

**Tipos de datos:**
[Aqui encuentras la información](https://www.tecnologias-informacion.com/tipos-sql.html).

### Listar todas las tablas
```sql
SHOW TABLES;
```
> Para crear y mostrar tablas, tienes que estar dentro de una base de datos.
### Muestra la tabla en ejecucion
```sql
SELECT DATABASE();
```
### Eliminar tabla
```sql
DROP TABLE alumnos;
```
### Muestra las columnas de una tabla y sus requerimientos
```sql
SHOW COLUMNS FROM alumnos;
```
```sql
DESC alumnos;
```
### Genera una tabla nueva desde una ya existente
```sql
CREATE TABLE usuarios LIKE alumnos;
```
> Las columnas y requirimientos de ambas tablas seran identicas

### Crear documento .sql exportable
**Unicamente una base de datos**

Contenido.sql:
```sql
DROP DATABASE escuela;
CREATE DATABASE escuela;
USE escuela;

/* Creacion o eliminacion de tablas */

/* Iserto, lectura, edicion o eliminacion de valores de las tablas etc. */
```
**Abrir el documento en la consola**
```sql
SOURCE C:\Users\user1\Desktop\mysql\ruta\Contenido.sql
```
### Eliminar una base de datos solo si existe
```sql
DROP DATABASE IF EXIST escuela;
```
### Crear una base de datos solo si no existe
```sql
CREATE DATABASE IF NOT EXIST escuela;
```
### Crear una tabla solo si no existe
```sql
CREATE TABLE IF NOT EXIST alumnos;
```

---
## CRUD

### Insertar datos en una tabla
```sql
INSERT INTO alumnos (alumno_id, nombre, apellido, genero, fecha_nacimiento, pais_origen) VALUES (1, "Juan", "Bautista", "H", "1998-04-24", "México");
```
Insert para multiples datos
```sql
INSERT INTO alumnos (alumno_id, nombre, apellido, genero, fecha_nacimiento, pais_origen) VALUES 
(1, "Juan", "Bautista", "H", "1998-04-24", "México"), (2, "Carlos", "Chavez", "H", "1999-09-29", "Ecuador"),(3, "Emily", "Lopez", "M", "2002-02-22", "Colombia");
```

### Lectura de datos de una tabla
```sql
SELECT * FROM alumnos;
```
Muestra:

|alumno_id|nombre|apellido|genero|fecha_nacimiento|pais_origen|
|---------|------|--------|------|----------------|-----------|
|1|Juan|Bautista|H|1998-04-24|México|
|2|Carlos|Chavez|H|1999-09-29|Ecuador|
|3|Emily|Lopez|M|2002-02-22|Colombia|
```sql
SELECT nombre, apellido FROM alumnos;
```
Muestra:

|nombre|apellido|
|------|--------|
|Juan|Bautista|
|Carlos|Chavez|
|Emily|Lopez|

Muestra todos los datos del alumno de nombre Carlos:
```sql
SELECT * FROM alumnos WHERE nombre = 'Carlos';
```
> Simbolos de condiciones: =, <, >, <=, >=, != o <>. SELECT columnas FROM nomTabla WHERE atributo condición valor.

Muesta todos los datos de los alumnos que tengan de nombre Emily y edad mayor o igual a 20 años:
```sql
SELECT * FROM alumnos WHERE nombre = 'Emily' AND edad >= 20;
```
> AND OR y NOT

Muestra la calificacion de los alumnos que tengan de calificacion 5 y pertenescan al grupo 1, o a los alumnos que tengan el estado reprobado y pertenescan al grupo 1:
```sql
SELECT calificacion FROM alumnos WHERE (calificacion = 5 AND grupo = 1) OR (estado = reprobado AND grupo = 1);
```
Muestra todos los datos de los alumnos con estado nulo:
```sql
SELECT * FROM alumnos WHERE estado IS NULL;
```
```sql
SELECT * FROM alumnos WHERE estado <=> NULL;
```
Muestra todos los datos de los alumnos sin estado nulo:
```sql
SELECT * FROM alumnos WHERE estado IS NOT NULL;
```
Muestra el apellido de todos los alumnos cuya fecha de nacimiento sea entre 1910-01-01 y 2010-12-31:
```sql
SELECT apellido FROM alumnos WHERE fecha_nacimiento BETWEEN '1910-01-01' AND '2010-12-31';
```
Muestra el genero de los alumnos cuyos nombres son Juan, Carlos, Emily, Matias: (lista)
```sql
SELECT genero FROM alumnos WHERE nombre IN ("Juan", "Carlos", "Emily", "Matias");
```
Muestra todos los nombres diferentes de los alumnos:
```sql
SELECT DISTINCT nombre FROM alumnos;
```
Coloca un nombre mas corto a las columnas alumno_id y fecha_nacimiento al hacer una consulta, tambien haslo con la tabla:
```sql
SELECT alumns.alumno_id AS alumId, alumns.fecha_nacimiento AS fechNa FROM alumnos As alumns;
```

### Edición de datos de una tabla
Agregar una columna:
```sql
ALTER TABLE alumnos ADD calificacion_global INT UNSIGNED NOT NULL DEFAULT 5;
```
Eliminar una columna:
```sql
ALTER TABLE alumnos DROP COLUMN calificacion_global;
```
Renombrar tabla:
```sql
ALTER TABLE alumnos RENAME alumns;
```
Modifica un tipo de dato de una tabla: (telefono INT)
```sql
ALTER TABLE alumnos MODIFY telefono VARCHAR(50);
```
Añadir una llave primaria:
```sql
ALTER TABLE alumnos ADD id INT UNSIGNED NOT NULL AUTO_INCREMENT, ADD PRIMARY KEY (id);
```
Añadir una llave foranea:
```sql
ALTER TABLE alumnos ADD FOREIGN KEY(maestro_id) REFERENCES maestros(maestro_id);
```
Eliminar una llave foranea:
```sql
ALTER TABLE alumnos DROP FOREIGN KEY maestro
_id;
```
Coloca una columna apodo con el valor Pepe a todos los registros de la tabla alumnos, los cuales tengan de nombre Jose, tambien ponles 10 en calificacion:
```sql
UPDATE alumnos SET apodo = 'Pepe', calificacion = 10 WHERE nombre = Jose;
```

### Eliminacion de datos de una tabla

Elimina todos los registros de la tabla alumnos:
```sql
DELETE FROM alumnos;
```
Elimina todos los registros de la tabla alumnos que sean menores de 20 años:
```sql
DELETE FROM alumnos WHERE edad < 20;
```
Eliminacion en cascada:
```sql
  FOREIGN KEY (maestro_id) REFERENCES maestros(maestro_id) ON DELETE CASCADE

  DELETE FROM alumnos WHERE maestro_id = 1;
```
> No se puede eliminar fasilmente ya que su id esta enlazada con otra tabla. Al realizar este proceso, la eliminacion de este id impactara a todos sus enlaces.

Elimina los registros de la tabla alumnos desde 0:
```sql
TRUNCATE TABLE alumnos;
```

---
## Restricciones
### invalidar campos nulos
```sql
CREATE TABLE alumnos(
  numbre VARCHAR(50) NOT NULL,
  apellido VARCHAR(50) NOT NULL
);
```
### Invalidar campos repetidos
```sql
CREATE TABLE alumnos(
  rfc VARCHAR(10) UNIQUE,
  curp VARCHAR(18) UNIQUE
);
```
```sql
CREATE TABLE alumnos(
  rfc VARCHAR(10),
  curp VARCHAR(18),
  CONSTRAINT unique_combinacion UNIQUE (rfc, curp)
);
```
### Valores por defecto
```sql
CREATE TABLE alumnos(
  fecha_creacion DATETIME DEFAULT current_timestamp
);
```
### Invalidar numeros negativos
```sql
CREATE TABLE alumnos(
  edad INT UNSIGNED
);
```
### Validar solo datos especificos
```sql
CREATE TABLE alumnos(
  genero ENUM('M','F')
);
```
> Limite de 4 opciones
### Llave primaria
```sql
CREATE TABLE alumnos(
  alumno_id INT UNSIGNED PRIMARY KEY AUTO_INCREMENT
);
```
```sql
CREATE TABLE alumnos(
  alumno_id INT UNSIGNED AUTO_INCREMENT,
  PRIMARY KEY(usuario_id)
);
```
> Las consultas por este medio son más rapidaz y es un atributo unico por tabla. El auto_increment aumenta su valor en 1 por incercion.
### Llaves foraneas
```sql
CREATE TABLE alumnos(
  alumno_id INT PRIMARY KEY ,
  maestro_id INT UNSIGNED NOT NULL,
  FOREIGN KEY (maestro_id) REFERENCES maestros(maestro_id)
);
```
> Permite Enlazar dos tablas por medio de las llaves primarias de ambas tablas.

> Ambas llaves primarias deben existir.
---
## Funciones

### CONCAT( )
Muestra el nombre completo de los alumnos:
```sql
SELECT CONCAT(nombre, " ", apellido) AS nombre_completo FROM alumnos;
```
### LENGTH( )
Muestra todos los datos de los alumnos cuyo nombres no superen los 4 caracteres:
```sql
SELECT * FROM alumnos WHERE LENGTH(nombre) < 5;
```
### UPPER( ) y LOWER( )
Muestra el nombre de los alumnos en mayusculas y minusculas.
```sql
SELECT UPPER(nombre) AS nomMayus, LOWER(nombre) AS nomMinus from alumnos;
```
### TRIM( )
Elimina los espacios sobrantes en los apellidos de la tabla alumnos:
```sql
SELECT TRIM(apellido) from alumnos;
```
### LEFT( ) y RIGHT( )
Busca los nombres de los alumnos cuyos apellidos empiecen y terminen con los strings "ju" y "an".
```sql
SELECT nombre FROM alumnos WHERE LEFT(apellido,2) AS substring_izq = "Ju" AND RIGHT(apellido,2) AS substring_der = "an";
```
### RAND( )
Genera un numero aleatorio entre 0 y 1.
```sql
SELECT RAND();
```
### ROUND( )
Redondea valores decimales a enteros.
```sql
SELECT ROUND(RAND()*100);
```
### TRUNCATE( )
Concerba solo los decimales que le pides (1.23)
```sql
SELECT TRUNCATE(1.2345,2);
```
### POW( )
Eleva a una potecia un numero (2X2X2=8)
```sql
SELECT POW(2,3);
```
### NOW( )
Muestra la fecha actual
```sql
SELECT NOW();
```
### SECOND( ), MINUTE( ), HOUR( ), DAYOFWEEK( ), DAYOFMONTH( ), MONTH( ), DAYOFYEAR( ) y YEAR( )
```sql
SET @now = NOW();
```
Muestra solo los segundos, minutos, horas, dia de la semana, dia del mes, mes, dia del año y año de la fecha actual:
```sql
SELECT SECOND(@now), MINUTE(@now), HOUR(@now), DAYOFWEEK(@now), DAYOFMONTH(@now), MONTH(@now), DAYOFYEAR(@now), YEAR(@now);
```
Sumar o restar en fechas
```sql
SELECT @now + INTERVAL 30 DAY;
```
> SECOND, MINUTE, HOUR, DAY, WEEK, MONTH y YEAR
### CURDATE( )
Muestraa la fecha actual sin la hora.
```sql
SET @now = CURDATE();
```
### IF
Respuesta ante una condición
```sql
SELECT IF(10>9,"El numero si es mayor","el numero no es mayor");
```
### IFNULL( )
Si el estado del alumno es nulo. Retornar "sin evaluacion".
```sql
SELECT IFNULL(estado,"Sin evaluación") from alumnos;
```
### Crear una funcion
```sql
DELIMITER /
/* Cambia el simbolo que determina el cierre de la consulta */

CREATE FUNCTION agregar_dias(fecha DATE, dias INT)
RETURNS DATE
BEGIN
  RETURN fecha + INTERVAL dias DAY;
  /* Agrgar sentencias en una fincion */
  /* SET @paginas = (SELECT (ROUND(RAND()*100)*4));*/
  /* return @paginas */
END//

DELIMITER ;

SELECT agregar_dias(fecha_nacimiento, 90) from alumnos;
/* Implementacion de función */
```
### Listar funciones creadas
```sql
SELECT name FROM mysql.proc WHERE db = database() AND type = 'FUNCTION';
/* base de datos mysql y tabla proc */
```
> En mysql.proc se encuentran todos los procesos de las bases de datos. database() devuelve la base de datos en la que nos encontramos.

### Eliminar funcion
```sql
DROP FUNCTION agregar_dias;
```
---
## Sentencias avanzadas

### LIKE "xx%", LIKE "%xx", LIKE "%xx%", etc
Encuentra un substrings al principio de un valor en una tabla:
```sql
SELECT * FROM alumnos WHERE apellido Like "Gue%";
```
Encuentra un substrings al final de un valor en una tabla:
```sql
SELECT * FROM alumnos WHERE apellido Like "%ro";
```
Encuentra un substrings dentro de un valor en una tabla:
```sql
SELECT * FROM alumnos WHERE apellido Like "%rre%";
```
Muestra todos los alumnos que tengan en su nombre 5 caracteres y que en su segundo caracter tenga una u:
```sql
SELECT * FROM alumnos WHERE apellido LIKE "_u___"
/* 5 espacios y con una u en la segunda pocicion */
```
Muestra todos los alumnos que tengan la letra e en su tercer caracter del apellido:
```sql
SELECT * FROM alumnos WHERE apellido LIKE "__e%";
```
### REGEXP
Muestra todos los alumnos que tengan la letra e,a,j y r en su primer caracter del apellido:
```sql
SELECT * FROM alumnos WHERE apellido REGEXP "^[EAJR]";
```
### Ordenar Registros (Acendente)
```sql
SELECT apellido FROM alumnos WHERE ORDER BY apellido ASC;
```
### Ordenar Registros (Decendente)
```sql
SELECT apellido FROM alumnos WHERE ORDER BY apellido DESC;
```
### Limitar registros
```sql
SELECT apellido FROM alumnos LIMIT 15;
```
> Los primeros 15 registros
```sql
SELECT apellido FROM alumnos LIMIT 15,15;
```
> Desde el registro 15 mostrar, los 15 siguientes

### Funciones de agregación
Cuenta el total de alumnos en la tabla:
```sql
SELECT COUNT(*) AS total FROM alumnos;
```
Cuenta los alumnos ya evaluados
```sql
SELECT COUNT(estado) AS total FROM alumnos;
```
Suma la edad de todos los alumnos:
```sql
SELECT SUM(edad) AS total FROM alumnos;
```
Muestra el alumno mayor:
```sql
SELECT Max(edad) AS mayor FROM alumnos;
```
Muestra el alumno menor:
```sql
SELECT MIN(edad) AS menor FROM alumnos;
```
Muestra el promedio de todas las edades:
```sql
SELECT AVG(edad) AS resultado FROM alumnos;
```
### Agrupamiento
Muestra la suma de todas las materias cursadas por alumno:
```sql
SELECT alumno_id, SUM(materias) from alumnos GROUP BY alumno_id;
```
Muestra al alumno con mayor cantidad de materias:
```sql
SELECT alumno_id, SUM(materias) AS total from alumnos GROUP BY alumno_id ORDER BY total DESC LIMIT 1;
```
Muestra la suma de todas las materias cursadas por los alumnos que tengan más de 15 materias:
```sql
SELECT alumno_id, SUM(materias) from alumnos GROUP BY alumno_id HAVING SUM(materias) > 15;
```
### Unir resultados
Muestra los nombres completos de los alumnos y maestros registrados en las tablas:
```sql
SELECT CONCAT(nombre," ", apellido) AS nombre_completo FROM alumnos UNION SELECT CONCAT(nombre," ", apellido) AS nombre_completo FROM maestros;
```
> Deben tener el mismo numero de columnas ambas tablas.
### Consultas anidadas
Muestra los nombres completos de los alumnos que tengan una suma de creditos superior al promedio de los creditos totales:
```sql
SELECT CONCAT(nombre, " ", apellido) FROM alumnos WHERE alumno_id IN (
  SELECT alumno_id FROM proyectos GROUP BY alumno_id HAVING SUM(creditos) > (
    SELECT AVG(creditos) FROM proyectos
  )
);
```
### Validar registros existentes
Muestra el mensaje "Inscrito" si el alumno con el curp x esta registrado y "Sin registro" en dado caso que no exista:
```sql
SELECT IF(
  EXISTS(
    SELECT alumno_id FROM alumnos WHERE curp = "xxxxxxxxx"
  ), "REGISTRADO", "Sin registro"
) AS mensaje
```
---
## JOINS
Nos permite interactuar con 2 o más tablas relacionadas.
### INNER JOIN 
Muestra el nombre de los profesores de cada alumno y a sus alumnos correspondientes:
```sql
SELECT alumnos.nombre, maestros.nombre FROM alumnos INNER JOIN maestros ON alumnos.maestro_id = maestros.maestro_id;
```
> El primer elemento debe tener una llave foranea, en este caso en la tabla de alumnos
```sql
SELECT alumnos.nombre, maestros.nombre FROM alumnos INNER JOIN maestros USING(maestro.id);
```
> Usar USING en lugar de ON como alternativa, solo si se concerban las caracteristicas de la primera consulta.

Muestra el nombre de los profesores de cada alumno y a sus alumnos correspondientes si los alumnos cuentan con una calificacion mayor a 5:
```sql
SELECT alumnos.nombre, maestros.nombre FROM alumnos INNER JOIN maestros ON alumnos.maestro_id = maestros.maestro_id AND alumnos.evaluacion > 5;
```
### Tabla central
Para el uso de las siguientes propiedades debe haber una tabla intermediaria por cada relacion de tablas y esta no necesariamente debe tener una llave primaria individual. Esta tabla debe tener dos llavez foraneas apuntando a las tablas por relacionar.
```sql
CREATE TABLE materia (
  alumno_id INT UNSIGNED NOT NULL,
  maestro_id INT UNSIGNED NOT NULL,
  FOREIGN KEY(alumno_id) REFERENCES alumnos.alumno_id,
  FOREIGN KEY(maestro_id) REFERENCES maestros.maestro_id,
  asignatura VARCHAR(30),
  fecha_asignacion DATETIME DEFAULT current_timestamp
)
```
### LEFT JOIN
Usaremos la primera tabla y la tabla central.

Muestra el nombre de los alumnos que esten inscritos a la materia de fisica y quimica, tambien muestra el id dle profesor.
```sql
SELECT alumnos.nombre, materia.asignatura, materia.maestro_id FROM alumnos LEFT JOIN materias ON alumnos.alumno_id = materias.alumno_id WHERE materias.maestro_id IS NOT NULL;
```
### RIGHT JOIN
Usaremos la primera tabla y la tabla central solo que sera de forma inversa.
Muestra el nombre de los alumnos que esten inscritos a la materia de fisica y quimica, tambien muestra el id dle profesor.
```sql
SELECT alumnos.nombre, materia.asignatura, materia.maestro_id FROM materias LEFT JOIN alumnos ON alumnos.alumno_id = materias.alumno_id WHERE materias.maestro_id IS NOT NULL;
```
### Multiples JOIN 
Muestra el nombre del alumno, sus asignaturas y el nombre de su profesor. asignaturas aprobadas, y alumnos con las iniciales de la A - G
```sql
SELECT alumnos.nombre, maestros.nombre, materias.asignatura FROM alumnos 
INNER JOIN materias ON alumnos.alumno_id = materias.alumno_id
INNER JOIN maestros ON materias.maestro_id = maestro.maestro_id
AND alumnos.evaluacion > 5 AND alumnos.nombre REGEXP "^[ABCDEFG]"
```
### CROSS JOIN
Retorna todos los registros de todas las tablas implicadas en la unión, devuelve el producto cartesiano. (combina todos los elementos de la tabla 1 con los elementos de la tabla 2):
```sql
SELECT alimentos.nombre, bebidas.nombre from alimentos CROSS JOIN bebidas DESC;
```
---
## Vistas
Una vista es el conjunto de resultados de una consulta almacenada en los datos. Es una consulta que se presenta como una tabla a partir de un conjunto de tablas en una base de datos relacional. Las vistas tienen la misma estructura que una tabla: filas y columnas. (una vista es una tabla virtual creada a partir de un query)

### Crear una vista de una consulta
```sql
CREATE VIEW nom_vista_vw AS
/* Agregar una consulta*/
```
> se muestra al colocar show tables

### Eliminar vista
```sql
DROP VIEW nom_vistas_vw;
```

### Editar vista
```sql
CREATE OR REPLACE VIEW nom_vista_vw AS
/* Agregar una consulta */
```
---
## Procedimientos almacenados
Realiza acciones especificas sin retornar.

Muestra los PROCEDURE
```sql
SHOW PROCEDURE STATUS WHERE db = database() AND type = 'PROCEDURE'\G
```
### Crear procedimiento
```sql
DELIMITER //

CREATE PROCEDURE prestamo(usuario_id INT, libro_id INT)
BEGIN 
  INSERT INTO libros_usuarios(libro_id, usuario_id) VALUES (libro_id, usuario_id);
  UPDATE libros SET stoks = stoks - 1 WHERE libros.libro_id = libro_id;
END//

DELIMITER ;
```

Ejecutar PROCEDURE
```sql
CALL prestamo(3,20);
```
### Eliminar procedimiento
```sql
DROP PROCEDURE prestamo;
```
### Obtener valores
```sql
DELIMITER //

CREATE PROCEDURE prestamo(usuario_id INT, libro_id INT, OUT cantidad INT)
BEGIN 
  INSERT INTO libros_usuarios(libro_id, usuario_id) VALUES (libro_id, usuario_id);
  UPDATE libros SET stock = stock - 1 WHERE libros.libro_id = libro_id;
  SET cantidad = (SELECT stock FROM libros WHERE libros.libro_id = libro_id);
END//

DELIMITER ;
```

### Condiciones
```sql
DELIMITER //

CREATE PROCEDURE prestamo(usuario_id INT, libro_id INT, OUT cantidad INT)
BEGIN
  SET cantidad = (SELECT stock FROM libros WHERE libros.libro_id = libro_id);

  IF cantidad > 0 THEN /* inicion condicion */
    INSERT INTO libros_usuarios(libro_id, usuario_id) VALUES (libro_id, usuario_id);
    UPDATE libros SET stock = stock - 1 WHERE libros.libro_id = libro_id;
    SET cantidad = cantidad - 1;
  ELSE
    SELECT "No es posible realizar el prestamo" AS error;
  END IF;  /* fin condicion */
END//

DELIMITER ;
```
> Puedes utilizar operadores logicos AND OR NOT y ELSE IF

### Casos
```sql
CREATE PROCEDURE tipo_lector(usuario_id INT)
BEGIN
  SET @cantidad = (SELECT COUNT(*) FROM libros_usuarios WHERE libros_usuarios.usuario_id = usuario_id);
  CASE
    WHEN @cantidad > 20 THEN
      SELECT "Fanatico" AS mensaje;
    WHEN @cantidad > 10 AND @cantidad < 20 THEN
      SELECT "Afionado" AS mensaje;
    WHEN @cantidad > 5 AND @cantidad < 10 THEN
      SELECT "Promedio" AS mensaje;
    ELSE
      SELECT "Nuevo" AS mensaje;
  END CASE;
END//
```
### Bucles
```sql
/* WHILE */
CREATE PROCEDURE libros_azar_1()
BEGIN
  SET @iteraciones= 0;

  WHILE @iteraciones < 5 DO
    SELECT libro_id, titulo FROM libros ORDER BY RAND() LIMIT 1;
    SET @iteraciones = @iteraciones + 1;
  END WHILE;
END//

/* REPEAT */
CREATE PROCEDURE libros_azar_2()
BEGIN
  SET @iteraciones= 0;

  REPEAT
    SELECT libro_id, titulo FROM libros ORDER BY RAND() LIMIT 1;
    SET @iteraciones = @iteraciones + 1;

    UNTIL @iteraciones >= 5
  END REPEAT;

END//
```
> WHILE se repetira hasta que la condicion ya no sea valida y REPEAT se repetira hasta que cumpla la condicion.

Investigar por actualizacion

---
## Transacciones
 Ejecutara las consultas como uno solo.

### Iniciar Transacción
```sql
START TRANSACTION;
/* Consultas */
COMMIT;
```
> Los cambios seran irreversibles

En caso de que la consulta no exista y haya un error usar ROLLBACK para reiniciar la transaccion desde antes de la consulta erronea:
```sql
ROLLBACK;
```
### Transaccion y procedimientos almacenados
```sql
DELIMITER //

CREATE PROCEDURE prestamo(usuario_id INT, libro_id INT)
BEGIN 
  DECLARE EXIT HANDLER FOR SQLEXCEPTION --Ocurre un error
  BEGIN
    -- Todas las consultas que necesites
    ROLLBACK;
  END;
  
  START TRANSACTION;
  INSERT INTO libros_usuarios(libro_id, usuario_id) VALUES (libro_id, usuario_id);
  UPDATE libros SET stoks = stoks - 1 WHERE libros.libro_id = libro_id;
  COMMIT;
END//

DELIMITER ;
```
---
## Motores de almacenamiento en MySQL

Investigar sobre MyISAM e InnoDB
Eventos, Cursores, Respaldo de información, generar nuevos usuarios en mySQL

## TRIGGERS

### Creación
```sql
CREATE TABLE autores (...);
ALTER TABLE ADD COLUMN catidad_libros INT DEFAULT 0;

DELIMITER //
-- Nombre de acuerdo al tiempo, tipo y funcion
CREATE TRIGGER after_insert_actualizacion_libros
--AFTER: Despues. BEFORE: Antes.
AFTER INSERT ON libros
FOR EACH ROW -- Por cada linea de los registros afectados
BEGIN
  UPDATE autores SET cantidad_libros = cantidad_libros + 1 WHERE autor_id = NEW.autor_id;
END//

DELIMITER ;
```
### Eliminacion
```sql
CREATE TABLE autores (...);
ALTER TABLE ADD COLUMN catidad_libros INT DEFAULT 0;

DELIMITER //
-- Nombre de acuerdo al tiempo, tipo y funcion
CREATE TRIGGER after_delete_actualizacion_libros
--AFTER: Despues. BEFORE: Antes.
AFTER DELETE ON libros
FOR EACH ROW -- Por cada linea de los registros afectados
BEGIN
  UPDATE autores SET cantidad_libros = cantidad_libros - 1 WHERE autor_id = OLD.autor_id;
END//

DELIMITER ;
```
### Actualizacion
```sql
CREATE TABLE autores (...);
ALTER TABLE ADD COLUMN catidad_libros INT DEFAULT 0;

DELIMITER //
-- Nombre de acuerdo al tiempo, tipo y funcion
CREATE TRIGGER after_UPDATE_actualizacion_libros
--AFTER: Despues. BEFORE: Antes.
AFTER UPDATE ON libros
FOR EACH ROW -- Por cada linea de los registros afectados
BEGIN
  IF NEW.autor_id != OLD.autor_id THEN
    UPDATE autores SET cantidad_libros = cantidad_libros + 1 WHERE autor_id = NEW.autor_id;
    UPDATE autores SET cantidad_libros = cantidad_libros - 1 WHERE autor_id = OLD.autor_id;
  END IF;
END//

DELIMITER ;
```
### Mostrar triggers
```sql
SHOW TRIGGERS\G;
```
### Eliminar TRIGGER
```sql
DROP TRIGGER libreria.after_UPDATE_actualizacion_libros;
```
> nombre de la db.nomTrigger