# Gobuster
> Gobuster es un escáner que busca objetos web existentes u ocultos. Funciona lanzando un ataque de diccionario contra un servidor web y analizando la respuesta.
## a
## Ejemplos de uso
Escanee un sitio web (-u http://192.168.0.155/) en busca de directorios utilizando una lista de palabras (-w /usr/share/wordlists/dirb/common.txt) e imprima las URL completas de las rutas descubiertas (-e):
```
root@kali:~# gobuster -e -u http://192.168.0.155/ -w /usr/share/wordlists/dirb/common.txt

Gobuster v1.2                OJ Reeves (@TheColonial)
=====================================================
[+] Mode         : dir
[+] Url/Domain   : http://192.168.0.155/
[+] Threads      : 10
[+] Wordlist     : /usr/share/wordlists/dirb/common.txt
[+] Status codes : 301,302,307,200,204
[+] Expanded     : true
=====================================================
http://192.168.0.155/blog (Status: 301)
http://192.168.0.155/index.html (Status: 200)
http://192.168.0.155/index (Status: 200)
http://192.168.0.155/photo (Status: 301)
http://192.168.0.155/wordpress (Status: 301)
=====================================================
```
## Referencias
* [KALITOOLS](https://tools.kali.org/web-applications/gobuster)
* 
