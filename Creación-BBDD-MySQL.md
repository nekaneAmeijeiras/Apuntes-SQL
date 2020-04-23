# Creación-BBDD-MySQL
## Índice
* [Ejercicio DDL 1 Proxecto Investigación](#Ejercicio-DDL-1-Proxecto-Investigación)
  * [Implementación en MySQL](#Implementación-en-MySQL)
* [Ejercicio Naves Espaciales](#Ejercicio-Naves-Espaciales)


 ## Ejercicio DDL 1 Proxecto Investigación
 
 A partir de este esquema relacional, realizaremos su implementación en MySQL.
 
  ![capturaEjercicio](https://github.com/davidgchaves/first-steps-with-git-and-github-wirtz-asir1-and-dam1/blob/master/exercicios-ddl/1-proxectos-de-investigacion/img/1-proxectos-de-investigacion-relacional.jpeg)
  
### Implementación en MySQL
Crearemos primero la base de datos mediante el comando  `CREATE DATABASE`  y posteriormente entraremos en ella mediante `USE` más el nombre de la base de datos para comenzar a crear todas las tablas dentro de esta.

![capturaEjPI1](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/ImagenesEjerciciosDDL/Capturas%20Proxectos_Investigaci%C3%B3n/Captura%201.PNG)

![capturaEjPI2](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/ImagenesEjerciciosDDL/Capturas%20Proxectos_Investigaci%C3%B3n/Captura%202.PNG)

![capturaEjPI3](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/ImagenesEjerciciosDDL/Capturas%20Proxectos_Investigaci%C3%B3n/Captura%203.PNG)

Al crear la tablas departamento y grupo antes que profesor, debemos utilizar el  `ALTER TABLE` para añadir a estas las claves foraneas procedentes de profesor como se puede ver el la siguiente imágen.

![capturaEjPI4](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/ImagenesEjerciciosDDL/Capturas%20Proxectos_Investigaci%C3%B3n/Captura%204.PNG)
