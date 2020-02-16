# Apuntes-SQL
## Índice
* [¿Que es SQL?](#que-es-sql)
* [DQL (Data Query Languaje)](#DQL-(Data-Query-Languaje))
  * [Estructura básica](#Estructura-básica)
  * [FROM](#from)
  * [WHERE](#where)
    * [Simbolos](#simbolos)
    * [IN](#in)
    * [BETWEEN](#between)
    * [LIKE](#like)
  * [ORDER BY](#order-by)
  * [DISTINCT](#distinct)
  * [HAVING](#having)
  * [GROUP BY](#group-by)
  * [ROUND](#round)
  * [LENGTH](#length)
  * [CONCAT](#concat)
  * [SUM](#sum)
  * [COUNT](#count)
  * [JOIN](#join)
    * [LEFT JOIN](#left-join)
    * [RIGHT JOIN](#right-join)
    * [INNER JOIN](#INNER-JOIN)
    
 ### ¿Que es SQL?
 Iniciales en inglés de Structured Query Lenguage, el SQL es un lenguaje de consulta orientado al manejo y administración de datos en una base de datos.
 Dentro de este podemos encotrar 6 areas diferentes que denominaremos como sublenguajes:
* **DQL** (Data Query Language): permite a los usuarios la consulta y manipulación de datos.
* **DML** (Data Manipulation Language): actúa sobre los datos que hay dentro de los objetos.
* **DDL** (Data Definition Language): actúa sobre los objetos de la base de datos.
* **TCL** (Transaction Control Language): permite administrar diferentes transacciones dentro de una base de datos.
* **DCL** (Data Control Language): permite crear roles, permisos e integridad referencial, además, de controlar el acceso a la base de datos.
* **SCL** (Session Control Language): permite la gestión de una sesión de usuario.

 ### DQL (Data Query Languaje)
 #### Estructura básica
 * **SELECT:** siempre será la primera fila de la consulta e indicará la columna de datos que queremos ver. Este debe de ir seguido del nombre de la columna.
 * **FROM:** siempre iniciará la segunda linea y le  dirá a la base de datos de que tabla queremos coger los datos, por lo que deberá ir precedido del nombre de la tabla o tablas de las que queramos sacar los datos.
 * La tercera linea podrá estar iniciada por **WHERE** o **HAVING** seguidos de la condición que le queramos dar a la consulta.
 * Otras lineas pueden comenzar por **GROUP BY** o **ORDER BY** que agruparan o ordenarán respectivamente los datos.
 
  ```ruby
  SELECT[DISTINCT] columna, columna ...
  FROM tabla, tabla ...
  [WHERE/HAVING condición]
  [GROUP BY/ORDER BY campo/s]
  
  ```
