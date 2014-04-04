
SSH sans mot de passe : export de clef public
=============================================

[source](http://www.linux-france.org/prj/edu/archinet/systeme/ch13s03.html)

L'utilisateur doit avoir une clef public, et l'enregistrer sur le serveur distant.  
Ainsi il n'aura plus besoin de taper son mot de passe à chaque connexion.


### Creer sa clef publique 

D'abord il faut verifier que la clef n'existe pas déja : 
    
    $ ls -l .ssh/  

Le fichier a un nom de type : _id\_dsa.pub, id\_rsa.pub, identity.pub_

Et la creer si elle n'existe pas
    
    $ ssh-keygen -t dsa

Il faut bien renseigner la pass phrase

### Enregistrer sa clef publique sur le serveur distant

Il faut copier la clef sur le serveur distant
    
    $ scp ~/.ssh/id_dsa.pub user@serveur:myid  

Ensuite se connecter dessus, pour rajouter la clef au fichier authorized_keys
    
    $ ssh user@serveur 
    $ cat myid >> .ssh/authorized_keys
    $ rm myid
    $ exit

A partir de la ssh demande la pass phrase si user se connect à serveur

### Utiliser ssh-agent pour s'affranchir de la passphrase

    $ eval $(ssh-agent)
    $ ssh-add
    $ ssh user@serveur ls

Et voila plus besoin de taper le mot de passe.  
Il est important de **lancer ssh-agent avant screen ou X ou ...** pour heriter des droits.



