# Local File Inclusion
> Los sitios web muchas veces también poseen vulnerabilidades, algunas muy conocidas que datan de hace tiempo y otras tal vez menos populares; en este caso hablaremos de Local File Inclusion (LFI) o, en español, Inclusión local de archivos.

> Esta técnica consiste en incluir ficheros locales, es decir, archivos que se encuentran en el mismo servidor de la web con este tipo de fallo -a diferencia de Remote File Inclusión o inclusión de archivos remotos (RFI) que incluye archivos alojados en otros servidores. Esto se produce como consecuencia de un fallo en la programación de la página, filtrando inadecuadamente lo que se incluye al usar funciones en PHP para incluir archivos.

## Ejemplo
Incluimos el archivo / etc / passwd, consulte el directorio y ruta para ver archivos más interesantes.
```
http://example.com/index.php?page=../../../etc/passwd
```
Para poder comprobar si un sitio es vulnerable se puede incluir un valor lógico.
```
http://localhost/index.php?page=
```
```
http://localhost/index.php?page=7se3
```
Si arroja un error como Warning: main()… o Warning: include()… o similar entonces es probable que sea vulnerable a RFI o LFI. 
## Código vulnerable
```
<?php
include $_GET[‘example’];
?>
```
## Codigo no vulnerable
```
<?php
include(‘example.php’);
?>
```
## Referencias
* [welivesecurity](https://www.welivesecurity.com/la-es/2015/01/12/como-funciona-vulnerabilidad-local-file-inclusion/)
