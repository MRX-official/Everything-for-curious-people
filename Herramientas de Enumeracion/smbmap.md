# SMBMap
> SMBMap permite a los usuarios enumerar las unidades compartidas de samba en todo un dominio. Enumera las unidades compartidas, los permisos de las unidades, los contenidos compartidos, la funcionalidad de carga / descarga, la coincidencia de patrones de descarga automática de nombres de archivo e incluso ejecute comandos remotos. Esta herramienta se diseñó teniendo en cuenta las pruebas de lápiz y está destinada a simplificar la búsqueda de datos potencialmente confidenciales en redes grandes.
## Instalar smbmap en Linux
```
sudo apt-get install smbmap
```
## Resumen de opciones
```
    ________  ___      ___  _______   ___      ___       __         _______
   /"       )|"  \    /"  ||   _  "\ |"  \    /"  |     /""\       |   __ "\
  (:   \___/  \   \  //   |(. |_)  :) \   \  //   |    /    \      (. |__) :)
   \___  \    /\  \/.    ||:     \/   /\   \/.    |   /' /\  \     |:  ____/
    __/  \   |: \.        |(|  _  \  |: \.        |  //  __'  \    (|  /
   /" \   :) |.  \    /:  ||: |_)  :)|.  \    /:  | /   /  \   \  /|__/ \
  (_______/  |___|\__/|___|(_______/ |___|\__/|___|(___/    \___)(_______)
 -----------------------------------------------------------------------------
     SMBMap - Samba Share Enumerator | Shawn Evans - ShawnDEvans@gmail.com   
                     https://github.com/ShawnDEvans/smbmap

optional arguments:
  -h, --help            show this help message and exit

Main arguments:
  -H HOST               IP of host
  --host-file FILE      File containing a list of hosts
  -u USERNAME           Username, if omitted null session assumed
  -p PASSWORD           Password or NTLM hash
  --prompt              Prompt for a password
  -s SHARE              Specify a share (default C$), ex 'C$'
  -d DOMAIN             Domain name (default WORKGROUP)
  -P PORT               SMB port (default 445)
  -v                    Return the OS version of the remote host
  --admin               Just report if the user is an admin
  --no-banner           Removes the banner from the top of the output
  --no-color            Removes color from output
  --no-update           Removes "Working on it..." update message from output

Command Execution:
  Options for executing commands on the specified host

  -x COMMAND            Execute a command ex. 'ipconfig /all'
  --mode CMDMODE        Set the execution method, wmi or psexec, default wmi

Shard drive Search:
  Options for searching/enumerating the share of the specified host(s)

  -L                    List all drives on the specified host, requires ADMIN
                        rights.
  -R [PATH]             Recursively list dirs, and files (no share\path lists
                        ALL shares), ex. 'C$\Finance'
  -r [PATH]             List contents of directory, default is to list root of
                        all shares, ex. -r 'C$\Documents and
                        Settings\Administrator\Documents'
  -A PATTERN            Define a file name pattern (regex) that auto downloads
                        a file on a match (requires -R or -r), not case
                        sensitive, ex '(web|global).(asax|config)'
  -g FILE               Output to a file in a grep friendly format, used with
                        -r or -R (otherwise it outputs nothing), ex -g
                        grep_out.txt
  --csv FILE            Output to a CSV file, used with -r or -R (otherwise it
                        outputs nothing), ex --csv shares.csv
  --dir-only            List only directories, ommit files.
  --no-write-check      Skip check to see if drive grants WRITE access.
  -q                    Quiet verbose output. Only shows shares you have READ
                        or WRITE on, and suppresses file listing when
                        performing a search (-A).
  --depth DEPTH         Traverse a directory tree to a specific depth. Default
                        is 5.
  --exclude SHARE [SHARE ...]
                        Exclude share(s) from searching and listing, ex.
                        --exclude ADMIN$ C$'

File Content Search:
  Options for searching the content of files (must run as root), kind of experimental

  -F PATTERN            File content search, -F '[Pp]assword' (requires admin
                        access to execute commands, and PowerShell on victim
                        host)
  --search-path PATH    Specify drive/path to search (used with -F, default
                        C:\Users), ex 'D:\HR\'
  --search-timeout TIMEOUT
                        Specifcy a timeout (in seconds) before the file search
                        job gets killed. Default is 300 seconds.

Filesystem interaction:
  Options for interacting with the specified host's filesystem

  --download PATH       Download a file from the remote system,
                        ex.'C$\temp\passwords.txt'
  --upload SRC DST      Upload a file to the remote system ex.
                        '/tmp/payload.exe C$\temp\payload.exe'
  --delete PATH TO FILE
                        Delete a remote file, ex. 'C$\temp\msf.exe'
  --skip                Skip delete file confirmation prompt

Examples:

$ python smbmap.py -u jsmith -p password1 -d workgroup -H 192.168.0.1
$ python smbmap.py -u jsmith -p 'aad3b435b51404eeaad3b435b51404ee:da76f2c4c96028b7a6111aef4a50a94d' -H 172.16.0.20
$ python smbmap.py -u 'apadmin' -p 'asdf1234!' -d ACME -H 10.1.3.30 -x 'net group "Domain Admins" /domain'
```
## Ejemplos de uso de smbmap
```
root@kali:~# smbmap -u victim -p s3cr3t -H 192.168.86.61
[+] Finding open SMB ports....
[+] User SMB session establishd on 192.168.86.61...
[+] IP: 192.168.86.61:445   Name: win7-x86.lan
    Disk                                                    Permissions
    ----                                                    -----------
    ADMIN$                                              NO ACCESS
    C$                                                  NO ACCESS
    IPC$                                                NO ACCESS
    Users                                               READ ONLY
```
## Referencias 
* [KALITOOLS](https://tools.kali.org/information-gathering/smbmap)
