##	http://www.trustonme.net/didactels/128.html

### Fichiers cachÃ©s

    > tar -cf archive.tar --exclude '.*' /home/monDossierPerso

DECOMPRESSION
=============

gzip -d /où_est/mon_fichier.gz
bzip2 -d /où_est/mon_fichier.bz2

tar -xzvf /où_est/mon_archive.tar.gz
tar -xjvf /où_est/mon_archive.tar.bz2

unzip /où_est/fichier.zip
unrar e /où_est/fichier.rar 
unace e /où_est/fichier.ace

  
  
________COMPRESSION 

gzip -9 /où_est/fichier
bzip2 -9 /où_est/fichier

tar -cvf nouvelle_archive.tar /mon_répertoire
tar -cvf nouvelle_archive.tar /où_est/mon_fichier
tar -cvf nouvelle_archive.tar /où_est/fichier1 /où_est/fichier2 .... /où_est/répertoireN

tar -czvf nouveau_nom.tar.gz /où_est/fichier1 /où_est/fichier2 .... /où_est/répertoireN
tar -cjvf nouveau_nom.tar.bz2 /où_est/fichier1 /où_est/fichier2 .... /où_est/répertoireN




