# Apuntes-SQL
## Índice
* [¿Que es SQL?](#que-es-sql)
* [DQL (Data Query Languaje)](#DQL-(Data-Query-Languaje))
  * [Cosas a tener en cuenta](#Cosas-a-tener-en-cuenta)
  * [Estructura básica](#Estructura-básica)
  * [Símbolos](#Símbolos)
  * [Comodines](#Comodines)
  * [Clausula SELECT](#Clausula_SELECT)
    * [DISTINCT](#DISTINCT)
    * [COUNT/SUM/AVG/MAX/MIN](#COUNT/SUM/AVG/MAX/MIN)
    * [JOINS](#JOINS)
  * [Clausula FROM](#Clausula_FROM)
    * [AS](#AS)
    * [JOIN](#JOIN)
  * [Clausula WHERE](#Clausula_WHERE)
    * [[NOT]IN](#[NOT]IN)
    * [[NOT]LIKE](#[NOT]LIKE)
    * [BETWEEN](#BETWEEN)
    * [LIMIT](#LIMIT)
    * [CONCAT](#CONCAT)
  * [Agrupación de filas](#Agrupación_de_filas)
    * [GROUP BY](#DISTINCT)
    * [HAVING](#COUNT/SUM/AVG/MAX/MIN)
  * [Clausula ORDER BY](#Clausula_ORDER_BY)
  * [Consultas anidadas](#Consultas_anidadas) 
  * [AND y OR](#AND_y_OR)
  * [IS[NOT]NULL](#IS[NOT]NULL) 
  
    
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
 * A partir de la tercera linea se iniciará por **WHERE**, **HAVING**, **GROUP BY** o **ORDER BY** 
 
  ```ruby
  SELECT[DISTINCT] columna, columna ...
  FROM tabla, tabla ...
  [WHERE condición]
  [GROUP BY campo/s]
  [HAVING condición]
  [ORDER BY campo/s];
  ```
#### Símbolos

* </> Menor o mayor que
* <=/>= Menor o igual o mayor o igual
* !< No menor que
* !> No mayor que
* = Igual
* <> Distinto

 ```ruby
 SELECT name
 FROM world
 WHERE population = 100000 ;
 ```
 En esta consulta se seleccionarían aquellos países cuya población fuese igual a 100000, pero este se puede cambiar por cualquiera de los otros símbolos en función a los datos a los que quieras acceder.

#### Comodines

Denominamos comodines a aquellos simbolos que se pueden utilizar para substituir a algún valor o parte de este.
* _ substituye a un único caracter ya sea número, letra, símbolo o espacio.
* % substituye uno o varios caracteres de un valor.
* El asterisco substituye a todos los valores de una tabla

```ruby
 SELECT name
 FROM world
 WHERE name = '_%' ;
 ```
 En esta consulta seleccionaríamos aquellos paises con un min de un caracter y un máximo ilimitado en función de cual sea el pais dentro de la tabla con mayor cantidad de caracteres.
 
#### Clausula SELECT
Como dijimos anteriormente, la clausula SELECT nos mostrará la columna de datos que pongamos después de este. Además, podemos añadir algunos filtros

#####  DISTINCT
Con DISTINCT podemos eliminar todos aquellos datos que aparezcan duplicados.

```ruby
 SELECT DISTINCT name
 FROM world
 WHERE name = '_%' ;
 ```
#####  COUNT/SUM/AVG/MAX/MIN
* **COUNT ():** Cuenta el número de filas devueltas en una consulta
* **SUM ():** Devuelve la suma de las colúmnas especificadas.
* **AVG ():** Calcula la media de las columnas especificadas.
* **MAX ():** Devuelve el valor más alto de la columna.
* **MIN ():** Devuelve el valor más bajo de la columna.

#### Clausula FROM
Como especificamos anteriormente, FROM especificará a la consulta de que tabla debe coger los datos. Dentro de este pueden añadirse diferentes filtros

#####  AS
El AS se utiliza para renombrar tanto relaciones como atributos, para ello debemos poner promero el nombre antiguo seguido de AS y después el nombre nuevo. Esta también puede aparecer en SELECT.

#####  JOINS

Utilizams JOIN para consultas en las que necesitamos los datos de más de una tabla. Estos pueden ser de varios tipos:
* **INNER JOIN:** que recoge solo aquellos elementos que no tengan valores nulos en ninguna de las tablas.
* **RIGHT JOIN:** recoge solo los elementos que no tengan valores nulos en la tabla de la derecha, aunque estos si tengan valores nulos en otras.
* **LEFT JOIN:** recoge solo los elementos que no tengan valores nulos en la tabla de la izquierda, aunque estos si tengan valores nulos en las otras.

```ruby
 SELECT actor.name
 FROM movie INNER JOIN casting ON movie.id=casting.movieid
            INER JOIN actor ON actor.id=casting.actorid
 WHERE movie.title='Tokyo Story' ;
 ```
 
#### Clausula WHERE
La clausula WHERE se va a componer de las condiciones que nosotros queramos especificar en la consulta, y para eso necesitaremos los siguientes filtros.


#####  [NOT] IN 
Comprueba si un elemento está dentro de una lista de elementos o no.Para eso los valores deben encontrarse dentro del paréntesis como se puede ver en el siguiente ejemplo.

```ruby
 SELECT name
 FROM world
 WHERE name [NOT]IN ('Francia','España') ;
 ```
#####  [NOT] LIKE
Compara una colúmna tipo caracter con una columna de caracteres.

#####  BETWEEN
La consulta te mostrará los resultados entre dos valores que tu escojas.
```ruby
 SELECT name, population
 FROM world
 WHERE population BETWEEN 10000 AND 12000;
 ```

#####  LIMIT
Nos permite limitar el número de resultados que queremos ofrecer.

#####  CONCAT
Nos permite encadenar los elementos que van dentro del paréntesis.En la siguiente consulta tendremos como resultado aquellos países que tengan como capital su nombre y algo más con uno o más caracteres.

```ruby
 SELECT name, capital
 FROM world
 WHERE capital LIKE CONCAT (name, '_%');
 ```

#### Agrupación de filas

#####  GROUP BY
Reorganiza el sentido lógico de la tabla, formando grupos en los cuales todas las filas tengan un mismo valor. Con esta clausula debemos especificar los nombres de las colúmnas que aparecen en SELECT.

#####  HAVING
La clausula HAVING funciona en cada grupo como WHERE en cada fila.

#### Clausula ORDER BY
Esta clausula puede ordenar los valores de manera ascendente o descendente (ASC/DESC). Se debe poner al final de la consulta.

#### Consultas anidadas
Una consulta puede estar compuesta por varias consultas, unas dentro de otras. Para hacer saber la SQL que existe una consulta anidada esta deberá estar puesta entre parentesis.
Es muy importante saber que estas van a ser leidas de "dentro hacia fuera", es decir, de la consulta anidada más interna hasta llegar a la consulta principal.

#### AND y OR
* **AND:** lo utilizamos como una y entre dos valores.
* **OR:** lo utilizamos como una o entre dos valores.

#### IS [NOT] NULL
Lo utilizamos para indicar dentro de una consulta si queremos o no añadir aquellos campos con valor nulo.


### DML (Data Manipulation Languaje)
Actua sobre los datos que hay dentro de los objetos
#### INSERT INTO
Sirve para insertar duplas nuevas dentro de una base de datos. Este, puede constar de values o select como se puede ver el la fórmula y los ejemplos siguientes.

```ruby
 INSERT INTO world (name, continent, area)
   VALUES ('Spain', 'Europe', 100), ('Portugal','Europe',10);
 ```
```ruby
 INSERT INTO world (name, continent, area)
   SELECT name, continent, area
   FROM world
   WHERE continent='Europe';
 ``` 
### DDL (Data Definition Languaje)
