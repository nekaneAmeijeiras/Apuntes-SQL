# Creación-BBDD-MySQL
## Índice
* [Ejercicio DDL 1 Proxecto Investigación](#Ejercicio-DDL-1-Proxecto-Investigación)
  * [Implementación en MySQL (Proxecto Investigación)](#Implementación-en-MySQL-(Proxecto-Investigación))
  * [Vista "Gráfica" de Proxecto Investigación](#Vista-"Gráfica"-de-Proxecto-Investigación)
* [Ejercicio DDL 2 Naves Espaciales](#Ejercicio-DDL-2-Naves-Espaciales)
  * [Implementación en MySQL(Naves Espaciales)](#Implementación-en-MySQL-(Naves-Espaciales))
  * [Vista "Gráfica" de Naves Espaciales](#Vista-"Gráfica"-de-Naves-Espaciales)


 ## Ejercicio DDL 1 Proxecto Investigación
 
 A partir de este esquema relacional, realizaremos su implementación en MySQL.
 
  ![capturaEjercicio](https://github.com/davidgchaves/first-steps-with-git-and-github-wirtz-asir1-and-dam1/blob/master/exercicios-ddl/1-proxectos-de-investigacion/img/1-proxectos-de-investigacion-relacional.jpeg)
  
### Implementación en MySQL
Crearemos primero la base de datos mediante el comando  `CREATE DATABASE`  y posteriormente entraremos en ella mediante `USE` más el nombre de la base de datos para comenzar a crear todas las tablas dentro de esta.
Después, creamos respectivamente, las tablas Sede, Departamento, Ubicación, Grupo, Profesor y Proxecto.

![capturaEjPI1](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/ImagenesEjerciciosDDL/Capturas%20Proxectos_Investigaci%C3%B3n/Captura%201.PNG)

![capturaEjPI2](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/ImagenesEjerciciosDDL/Capturas%20Proxectos_Investigaci%C3%B3n/Captura%202.PNG)

![capturaEjPI3](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/ImagenesEjerciciosDDL/Capturas%20Proxectos_Investigaci%C3%B3n/Captura%203.PNG)

Al crear la tablas departamento y grupo antes que profesor, debemos utilizar el  `ALTER TABLE` para añadir a estas las claves foraneas procedentes de profesor como se puede ver el la siguiente imágen.

![capturaEjPI4](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/ImagenesEjerciciosDDL/Capturas%20Proxectos_Investigaci%C3%B3n/Captura%204.PNG)

Creamos las tablas Participa, Programa y financia.

![capturaEjPI5](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/ImagenesEjerciciosDDL/Capturas%20Proxectos_Investigaci%C3%B3n/Captura%205.PNG)

Utilizamos el comando `ALTER TABLE` para añadir a financia dos claves foraneas, una que viene de proxecto y otra de programa.

![capturaEjPI6](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/ImagenesEjerciciosDDL/Capturas%20Proxectos_Investigaci%C3%B3n/Captura%206.PNG)

Por último borramos la clave foranea de profesor mediante `ALTER TABLE` y `DROP` y la volvemos a añadir modificada mediante `ALTER TABLE` y `ADD`.

![capturaEjPI7](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/ImagenesEjerciciosDDL/Capturas%20Proxectos_Investigaci%C3%B3n/Captura%207.PNG)


### Vista "Gráfica" de la Base de Datos

En la siguiente imágen se pueden ver todas las tablas de las que se compone la Base de Datos Proxectos_investigación, y más abajo cada una de las tablas y sus componentes.

![capturaEjPI8](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/ImagenesEjerciciosDDL/Capturas%20Proxectos_Investigaci%C3%B3n/Captura%208.PNG)

![capturaEjPI9](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/ImagenesEjerciciosDDL/Capturas%20Proxectos_Investigaci%C3%B3n/Captura%209.PNG)

![capturaEjPI10](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/ImagenesEjerciciosDDL/Capturas%20Proxectos_Investigaci%C3%B3n/Captura%2010.PNG)

![capturaEjPI11](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/ImagenesEjerciciosDDL/Capturas%20Proxectos_Investigaci%C3%B3n/Captura%2011.PNG)


## Ejercicio DDL 2 Naves Espaciales

A partir de este esquema relacional, realizaremos su implementación en MySQL.

![capturaEjercicio](https://github.com/davidgchaves/first-steps-with-git-and-github-wirtz-asir1-and-dam1/blob/master/exercicios-ddl/2-naves-espaciais/img/2-naves-espaciais-relacional.jpeg)

### Implementación en MySQL

Como en el ejercicio anterior comenzamos creando la base de datos y posteriormente, entraremos en ella para comenzar a crear las tablas. Después, creamos respectivamente, las tablas Servizo, Dependencia, Cámara, Tripulación, Planeta, Visita, Habita y Raza.

![capturaEjNE1](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/ImagenesEjerciciosDDL/Capturas%20Naves_Espaciales/Captura%201.PNG)

![capturaEjNE2](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/ImagenesEjerciciosDDL/Capturas%20Naves_Espaciales/Captura%202.PNG)

![capturaEjNE3](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/ImagenesEjerciciosDDL/Capturas%20Naves_Espaciales/Captura%203.PNG)

![capturaEjNE4](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/ImagenesEjerciciosDDL/Capturas%20Naves_Espaciales/Captura%204.PNG)

![capturaEjNE5](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/ImagenesEjerciciosDDL/Capturas%20Naves_Espaciales/Captura%205.PNG)

![capturaEjNE6](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/ImagenesEjerciciosDDL/Capturas%20Naves_Espaciales/Captura%206.PNG)

Utilizamos `ALTER TABLE` para añadir la clave foranea en en habita que proviene de raza y para añadir un comando `CHECK` en cámara.

![capturaEjNE7](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/ImagenesEjerciciosDDL/Capturas%20Naves_Espaciales/Captura%207.PNG)

### Vista "Gráfica" de la Base de Datos

En la siguiente imágen se pueden ver todas las tablas de las que se compone la Base de Datos Proxectos_investigación, y más abajo cada una de las tablas y sus componentes.

![capturaEjNE8](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/ImagenesEjerciciosDDL/Capturas%20Naves_Espaciales/Captura%208.PNG)

![capturaEjNE9](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/ImagenesEjerciciosDDL/Capturas%20Naves_Espaciales/Captura%209.PNG)

![capturaEjNE10](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/ImagenesEjerciciosDDL/Capturas%20Naves_Espaciales/Captura%2010.PNG)

![capturaEjNE11](https://github.com/nekaneAmeijeiras/Apuntes-SQL/blob/master/ImagenesEjerciciosDDL/Capturas%20Naves_Espaciales/Captura%2011.PNG)
