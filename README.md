# Apuntes-SQL
## Índice
* [¿Que es SQL?](#que-es-sql)
* [DQL (Data Query Languaje)](#DQL-(Data-Query-Languaje))
  * [Cosas a tener en cuenta](#Cosas-a-tener-en-cuenta)
  * [Estructura básica](#Estructura-básica)
  * [Símbolos](#Símbolos)
  * [Comodines](#Comodines)
  * [Clausula WHERE](#Clausula_WHERE)
    * [[NOT]IN](#[NOT]IN)
    * [[NOT]LIKE](#[NOT]LIKE)
    * [BETWEEN](#BETWEEN)
    * [LIMIT](#LIMIT)
    * [CONCAT](#CONCAT)
  
    
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

#####  CONCAT
