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
Después creamos, respectivamente, las tablas Sede, Departamento, Ubicación, Grupo, Profesor y Proxecto.

![capturaEjPI1](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/ImagenesEjerciciosDDL/Capturas%20Proxectos_Investigaci%C3%B3n/Captura%201.PNG)

![capturaEjPI2](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/ImagenesEjerciciosDDL/Capturas%20Proxectos_Investigaci%C3%B3n/Captura%202.PNG)

![capturaEjPI3](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/ImagenesEjerciciosDDL/Capturas%20Proxectos_Investigaci%C3%B3n/Captura%203.PNG)

Al crear la tablas departamento y grupo antes que profesor, debemos utilizar el  `ALTER TABLE` para añadir a estas las claves foraneas procedentes de profesor como se puede ver el la siguiente imágen.

![capturaEjPI4](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/ImagenesEjerciciosDDL/Capturas%20Proxectos_Investigaci%C3%B3n/Captura%204.PNG)

Creamos las tablas Participa, Programa y financia.

![capturaEjPI5](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/ImagenesEjerciciosDDL/Capturas%20Proxectos_Investigaci%C3%B3n/Captura%205.PNG)

Utilizamos el comando `ALTER TABLE` para añadir a financia dos claves foraneas, una que viene de proxecto y otra de programa.

![capturaEjPI6](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/ImagenesEjerciciosDDL/Capturas%20Proxectos_Investigaci%C3%B3n/Captura%206.PNG)

Por último borramos la clave foranea de profesor mediante `ALTER TABLE` y `DROP` y la volvemos a añadir modificada mediante `ALTER TABLE` y `ADD`

![capturaEjPI7](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/ImagenesEjerciciosDDL/Capturas%20Proxectos_Investigaci%C3%B3n/Captura%207.PNG)
