# DIRB
> DIRB es un escáner de contenido web. Busca objetos web existentes (y / u ocultos). Básicamente, funciona lanzando un ataque basado en diccionario contra un servidor web y analizando la respuesta.
## Ejemplo de uso
```
root@kali:~# dirb http://192.168.1.224/ /usr/share/wordlists/dirb/common.txt

-----------------
DIRB v2.21    
By The Dark Raver
-----------------

START_TIME: Fri May 16 13:41:45 2014
URL_BASE: http://192.168.1.224/
WORDLIST_FILES: /usr/share/wordlists/dirb/common.txt

-----------------

GENERATED WORDS: 4592                                                          

---- Scanning URL: http://192.168.1.224/ ----
==> DIRECTORY: http://192.168.1.224/.svn/                                                                                                                              
+ http://192.168.1.224/.svn/entries (CODE:200|SIZE:2726)                                                                                                                
+ http://192.168.1.224/cgi-bin/ (CODE:403|SIZE:1122)                                                                                                                    
==> DIRECTORY: http://192.168.1.224/config/                                                                                                                            
==> DIRECTORY: http://192.168.1.224/docs/                                                                                                                              
==> DIRECTORY: http://192.168.1.224/external/
``` 
