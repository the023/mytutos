
### Desactiver un service qui se lance au demarrage

    update-rc.d -f foo remove

### Rajouter un script de demarrage perso

http://jul.is.a.n0life.org/blog/post/2006/06/14/Ajouter-un-script-au-demarrage-de-la-Debian


    #!/bin/sh
    case "$1" in
      start|"") 
            # au démarrage
            ;;
      stop)   
            # à l'arret
            ;;
      *)
            echo "Usage: monscript [start|stop]" >&2
            exit 3
            ;;
    esac


Notez le case "$1" qui recupère le premier argument de la commande. 
Si l'argument est start ou qu'il n'y en a pas, alors on exécute ce qu'il y a au niveau de # au démarrage.  
Si l'argument est stop, ce qu'il y a au niveau de # à l'arret

Rajoutez lui le mode exécutable : 

    # chmod +x /etc/init.d/monscript
 
Vous pouvez à présent tester votre script directement depuis la console : 

    # /etc/init.d/monscript stop
    # /etc/init.d/monscript start
 
Ensuite, afin qu'il se lance automatiquement au démarrage, il faut 
le rajouter aux runlevels. Pour cela, utilisez simplement la commande 

update-rc.d : 

    # update-rc.d monscript defaults 99

update-rc.d possède un certain nombre d'options, nous utilisons les plus simples dans cet exemple :
    
    monscript : correspond au fichier bash /etc/init.d/monscript que nous venons de créer
    defaults : permet de couvrir tous les runlevels
    99 : est le niveau de priorité. 99 étant le plus faible et 1 le plus élevé. 

Le niveau de priorité correspondant à l'ordre lors du démarrage, les plus faibles étant exécutés en dernier.
Vous n'avez plus qu'à redémarrer pour essayer le tout!
