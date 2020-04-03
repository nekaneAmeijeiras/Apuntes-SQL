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
* [DML (Data Manipulation Languaje)](#DQL-(Data-Manipulation-Languaje))
  * [INSERT INTO](#INSERT-INTO)
  * [UPDATE](#UPDATE)
  * [DELETE FROM](#DELETE-FROM)
  * [Tipos de datos](#Tipos-de-datos)
* [DDL (Data Definition Languaje)](#DQL-(Data-Definition-Languaje))
  * [CREATE](#CREATE)
  * [Restricciones](#Restricciones)
  * [Tipos de datos](#Tipos-de-datos)
    * [Datos de cadena](#Datos-de-cadena)
    * [Datos numéricos](#datos-numéricos)
    * [Datos de fecha/hora](#datos-de-fecha/hora)
  * [ALTER TABLE](#ALTER-TABLE)
  
 ## ¿Que es SQL?
 Iniciales en inglés de Structured Query Lenguage, el SQL es un lenguaje de consulta orientado al manejo y administración de datos en una base de datos.
 Dentro de este podemos encotrar 6 areas diferentes que denominaremos como sublenguajes:
* **DQL** (Data Query Language): permite a los usuarios la consulta y manipulación de datos.
* **DML** (Data Manipulation Language): actúa sobre los datos que hay dentro de los objetos.
* **DDL** (Data Definition Language): actúa sobre los objetos de la base de datos.
* **TCL** (Transaction Control Language): permite administrar diferentes transacciones dentro de una base de datos.
* **DCL** (Data Control Language): permite crear roles, permisos e integridad referencial, además, de controlar el acceso a la base de datos.
* **SCL** (Session Control Language): permite la gestión de una sesión de usuario.

## DQL (Data Query Languaje)

### Cosas a tener en cuenta
 * Todas las consultas deben finalizar con un punto y coma.
 * Si en select o from hay que añadir varios elementos o tablas deben separarse por comas.
 * Debemos utilizar comillas simples para referirnos a un valor concreto de la tabla.
 * SQL diferencia entre mayusculas y minúsculas en cuanto a un dato o valor se refiere.
 * Para escribir los comandos utilizaremos mayúsculas.
 
### Estructura básica
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
### Símbolos

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

### Comodines

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
 
### Clausula SELECT
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

### Clausula FROM
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
 
### Clausula WHERE
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

### Agrupación de filas

#####  GROUP BY
Reorganiza el sentido lógico de la tabla, formando grupos en los cuales todas las filas tengan un mismo valor. Con esta clausula debemos especificar los nombres de las colúmnas que aparecen en SELECT.

#####  HAVING
La clausula HAVING funciona en cada grupo como WHERE en cada fila.

### Clausula ORDER BY
Esta clausula puede ordenar los valores de manera ascendente o descendente (ASC/DESC). Se debe poner al final de la consulta.

### Consultas anidadas
Una consulta puede estar compuesta por varias consultas, unas dentro de otras. Para hacer saber la SQL que existe una consulta anidada esta deberá estar puesta entre parentesis.
Es muy importante saber que estas van a ser leidas de "dentro hacia fuera", es decir, de la consulta anidada más interna hasta llegar a la consulta principal.

### AND y OR
* **AND:** lo utilizamos como una y entre dos valores.
* **OR:** lo utilizamos como una o entre dos valores.

### IS [NOT] NULL
Lo utilizamos para indicar dentro de una consulta si queremos o no añadir aquellos campos con valor nulo.


## DML (Data Manipulation Languaje)
Actua sobre los datos que hay dentro de los objetos.

### INSERT  INTO
Sirve para insertar duplas nuevas dentro de una base de datos. Este, puede constar de values o select como se puede ver el la fórmula y los ejemplos siguientes.
```ruby
 INSERT INTO <nombre-de-tabla> [(<Atributo1>, <Atributo2>, ...)]
   (VALUES (<valor1A>, <valor2A>, ...), (<valor1B>, <valor2B>, ...)
   ...|SELECT...);
 ```
**Ejemplos:**
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
 
 ### UPDATE
 Sirve para actualizar una dupla o sus atributos, es decir, sobre un dato en concreto.
 ```ruby
 UPDATE <nombre-de-tabla> 
   SET <Atributo1>= <Valor1>,
   <Atributo2>= <Valor2>;
 ```
**Ejemplo:**
```ruby
 UPDATE world 
   SET continent='Africa';
 ```
 
  ### DELETE FROM
 Sirve para eliminar duplas.
 ```ruby
 DELETE FROM <nombre-de-tabla> 
   [WHERE <predicado>];
 ```
**Ejemplo:**
```ruby
DELETE FROM world 
   WHERE continent='Europe';
 ```
 
## DDL (Data Definition Languaje)
Actua sobre los objetos de la base de datos (tablas).

### CREATE (USER | TABLE | DATABASE | SCHEMA | DOMAIN)
Mediante esta fórmula podemos crear usuarios (USER), tablas (TABLE), bases de datos (DATABASE, más restrictivo|SCHEMA) y nombrar tipos de datos dentro de una base de datos (DOMAIN).

```ruby
CREATE (DATABASE|SCHEMA)
  [IF NOT EXISTS] nombre-de-basedatos;
 ```
 ```ruby
CREATE DOMAIN nombre-de-dato    tipo-de-datos(n);
 ```
 ```ruby
CREATE TABLE <nombre-de-tabla>
  (<Atributo1>    <tipo-de-dato>    [NOT NULL],
   <Atributo2>    <tipo-de-dato>    [DEFAULT],...
   [PRIMARY KEY (clave-primaria)]
   [FOREING KEY (clave-foranea)
   REFERENCES (tabla-de-clave-foranea)]);
 ```
 **Ejemplo:**
```ruby
CREATE TABLE grupo
  (Nombre_grupo         VARCHAR(30),
   Nombre_departamento  VARCHAR(30),
   Áreas                VARCHAR(30)  NOT NULL,
   Lider                CHARD(9),
   PRIMARY KEY (Nombre_grupo, Nombre_departamento)
   FOREING KEY (Nombre_departamento)
   REFERENCES departamento);
 ```
### Restricciones
#### Clave primaria
```ruby
CONSTRAIN <nombre-de-restricción>
  PRIMARY KEY (<Atributos>);
 ```
 **Ejemplo:**
 ```ruby
CONSTRAIN PK-world
  PRIMARY KEY (world.name);
 ```
 #### Clave foranea
```ruby
CONSTRAIN <nombre-de-restricción>
  FOREING KEY (<Atributos>) 
   REFERENCE (<Atributo-referido>)
   <nombre-tabla-referencia>;
 ```
 **Ejemplo:**
 ```ruby
CONSTRAIN PK-world
  FOREING KEY (Nombre_departamento)
   REFERENCES departamento;
 ```
 ### Tipos de datos
 Las bases de datos soportan unos datos predefinidos, en función a lo que quieras que contenga cada celda.
 
 #### Datos de cadena:
 * **Char/character(n):** cadena de caracteres de longitud fija, con una longitud n especificada por el usuario.
 * **Varchar/character varying(n):** cadena de caracteres de longitud variable, con una longitud n especificada por el usuario.
 * **Graphics(n):** Cadena de caracteres de longitud fija con exactamente n caracteres.
 * **Vargraphics(n):** Cadena de longitud variable con hasta n caracteres.
 
 #### Datos numéricos:
 * **Int/integer:** número entero binario.
 * **Smallint:** número entero pequeño.
 * **Decimal(p,q):** número decimal de p dígitos y signo con q dígitos a la derecha del punto decimal.
 * **Float(p):** número en coma flotante.
 * **Money:** cantidad monetaria.
 
 #### Datos de fecha/hora:
 * **Date:** fecha (aaaammdd).
 * **Time:** hora (hhmmss).
 * **Timestamp:** Combinación de fecha y hora con una precisión de microsegundos.
 
### ALTER TABLE
Da la posibilidad de alterar o eliminar una tabla ya existente.
```ruby
ALTER TABLE <nombre-de-tabla>
  ADD <nombre-de-campo>    <tipo-de-datos>
  DROP <nombre-de-tabla>;
 ```

 ## Instalación de MySQL
 
 ### Descarga
 
 Para realizar la instalación de MySQL, primero debemos ir a su página oficial en el apartado de descargas.
 
 ![captura1](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/Captura%201.PNG)
 
 Como podemos ver en la imagen siguiente, escogemos el más pesado que cuenta con el paquete al completo.
 
 ![captura2](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/Captura%201.PNG)
 
Para que comience la descarga debemos presionar sobre lo que dice "No thanks, just start my download" y esperaremos hasta que esta finalice.
 
 ![captura3](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/Captura%203.PNG)
 
 ### Instalación
 
 Una vez descargado debemos pinchar para comenzar la instalación e  ir escogiendo los diferente apartados que se verán en las siguientes imágenes.
 
![captura4](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/Captura%204.PNG)
 
![captura5](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/Captura%205.PNG)
 
![captura6](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/Captura%206.PNG)

![captura7](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/Captura%207.PNG)

![captura8](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/Captura%208.PNG)

![captura9](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/Captura%209.PNG)

![captura10](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/Captura%2010.PNG)

![captura11](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/Captura%2011.PNG)

![captura12](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/Captura%2012.PNG)

![captura13](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/Captura%2013.PNG)

![captura14](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/Captura%2014.PNG)

![captura15](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/Captura%2015.PNG)

![captura16](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/Captura%2016.PNG)

![captura17](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/Captura%2017.PNG)

![captura18](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/Captura%2018.PNG)

![captura19](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/Captura%2019.PNG)

![captura20](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/Captura%2020.PNG)

![captura21](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/Captura%2021.PNG)

![captura22](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/Captura%2022.PNG)

![captura23](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/Captura%2023.PNG)

![captura24](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/Captura%2024.PNG)

![captura25](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/Captura%2025.PNG)

![captura26](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/Captura%2026.PNG)

![captura27](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/Captura%2027.PNG)
