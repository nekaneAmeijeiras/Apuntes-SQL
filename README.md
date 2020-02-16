# Apuntes-SQL
## Índice
* [¿Que es SQL?](#que-es-sql)
* [DQL (Data Query Languaje)](#DQL-(Data-Query-Languaje))
  * [Cosas a tener en cuenta](#Cosas-a-tener-en-cuenta)
  * [Estructura básica](#Estructura-básica)
  * [Símbolos](#Símbolos)
  * [Comodines](#Comodines)
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

#### Cosas a tener en cuenta
 * Todas las consultas deben finalizar con un punto y coma.
 * Si en select o from hay que añadir varios elementos o tablas deben separarse por comas.
 * Debemos utilizar comillas simples para referirnos a un valor concreto de la tabla.
 * SQL diferencia entre mayusculas y minúsculas en cuanto a un dato o valor se refiere.
 * Para escribir los comandos utilizaremos mayúsculas.
 
#### Estructura básica
 * **SELECT:** siempre será la primera fila de la consulta e indicará la columna de datos que queremos ver. Este debe de ir seguido del nombre de la columna.
 * **FROM:** siempre iniciará la segunda linea y le  dirá a la base de datos de que tabla queremos coger los datos, por lo que deberá ir precedido del nombre de la tabla o tablas de las que queramos sacar los datos.
 * La tercera linea podrá estar iniciada por **WHERE** o **HAVING** seguidos de la condición que le queramos dar a la consulta.
 * Otras lineas pueden comenzar por **GROUP BY** o **ORDER BY** que agruparan o ordenarán respectivamente los datos.
 
  ```ruby
  SELECT[DISTINCT] columna, columna ...
  FROM tabla, tabla ...
  [WHERE/HAVING condición]
  [GROUP BY/ORDER BY campo/s];
  ```
#### Símbolos

* </> Menor o mayor que
* <= Menor o igual
* >= Mayor o igual
* !< No menor que
* !> No mayor que
* = Igual
* <> Distinto

#### Comodines

Denominamos comodines a aquellos simbolos que se pueden utilizar para substituir a algún valor o parte de este.
* _ substituye a un único caracter ya sea número, letra, símbolo o espacio.
* % substituye uno o varios caracteres de un valor.
* El asterisco substituye a todos los valores de una tabla
