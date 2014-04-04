
RSYNC
=====

Arguments
---------

Explications -Haurov -n 

**-H** preserve hard links  
**-a** archive  
**-u** update  
**-o** preserver owner  
**-r** reccurssive  
**-v** verbose  
**-n** DRY-RUN  
**-t** preserve dates  


**--exclude-from="/path/file"**  exclude list of pattern  
**--exclude="pattern"**     exclude one or more files/dir  
**--exclude=".*"**    exclude hidden files  
    http://www.thegeekstuff.com/2011/01/rsync-exclude-files-and-folders/

**--progess**   affiche le l'avancement  
**--stats**     affiche des stats !  
**--omit-dir-times**    ne pas tenir compte des dates


Rsync et les PATH
-----------------

Il faut bien faire attention au path , pour copier le contenu de /source/
 
    rsync -n -av /source/ ./destination/ ; ### Path Correct, copie du contenu de source ;
    rsync -n -av /source/ ./destination ;  ### Path Correct, copie du contenu de source ;
    rsync -n -av /source ./destination/  ; ### Path incorect, copy du rep source/...  ;


Copie avec Progress + preserver dates

    rsync -rvt --progress --stats divx /mnt/hda/


Exemples
--------

[Rsync : les bases](http://www.demongeot.biz/tutos/Rsync.html)

Simple copie :

    rsync -aurv ./ user@serv:/home/dave/directory
 

Avec deletion:

    rsync -Haurov --delete /home/ /mnt/

Avec backup des deletes :
    
    rsync -Haurov --delete --backup --backup-dir=/mnt/deleted/ /home/ /mnt/mirror/

Avec exclude : 
    
    rsync -Haurov --stats --delete --backup --backup-dir=/mnt/deleted/ --exclude=/home/toto/**  /home/ /mnt/mirror/

Avec exclude depuis fichier 
    
    rsync --size-only -avc --exclude-from /home/user/file.exclude ./ user@serv:/path/

Depuis un serveru distant :
    
    rsync -Haurov --stats --delete --backup --backup-dir=/mnt/deleted/ --exclude=/home/toto/** root@Maitre:/home/ /mnt/mirror/ 


