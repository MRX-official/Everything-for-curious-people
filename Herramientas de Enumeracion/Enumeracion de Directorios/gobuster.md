# Gobuster
> Gobuster es un escáner que busca objetos web existentes u ocultos. Funciona lanzando un ataque de diccionario contra un servidor web y analizando la respuesta.
## Resumen de opciones
```
root@kali:~# gobuster -h
Usage of gobuster:
  -P string
        Password for Basic Auth (dir mode only)
  -U string
        Username for Basic Auth (dir mode only)
  -a string
        Set the User-Agent string (dir mode only)
  -c string
        Cookies to use for the requests (dir mode only)
  -e    Expanded mode, print full URLs
  -f    Append a forward-slash to each directory request (dir mode only)
  -fw
        Force continued operation when wildcard found (dns mode only)
  -i    Show IP addresses (dns mode only)
  -l    Include the length of the body in the output (dir mode only)
  -m string
        Directory/File mode (dir) or DNS mode (dns) (default "dir")
  -n    Don't print status codes
  -p string
        Proxy to use for requests [http(s)://host:port] (dir mode only)
  -q    Don't print the banner and other noise
  -r    Follow redirects
  -s string
        Positive status codes (dir mode only) (default "200,204,301,302,307")
  -t int
        Number of concurrent threads (default 10)
  -u string
        The target URL or Domain
  -v    Verbose output (errors)
  -w string
        Path to the wordlist
  -x string
        File extension(s) to search for (dir mode only)
```
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
