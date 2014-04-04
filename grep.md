
GREP
====

## Grep options

Before and After -A -B  
The -A1 tells grep to include 1 line after the match.   
    `grep -A1 "ERROR"`  
The -B includes lines before the match, in case you need that too.  
    `grep -B2 -A2 "ERROR"`
Afficher le numero de ligne -n  
    `grep -n boo file`  
Afficher le nom du fichier -l  
    `grep -l "boo" *`  
Exclure une pattern -v  
    `grep -v boo file`  
Compte le nombre d'occurence -c  
    `grep -c boo file`   
Ignore la casse -i  
    `grep -i boo file `  
Si pattern est dans un fichier -f  
    `grep -f monfichier file`  
PIPE  : que pour egrep  
    `egrep "boots|boot" file`

 
## repere qui accede a mysql

    cat /var/log/httpd/access_log |grep -n /phpMyAdmin/sql.php 


## Grep highlight only 
|grep -E "ERROR|$"



