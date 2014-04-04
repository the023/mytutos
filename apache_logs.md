

# Parser les Logs

  * Utiliser tail, cat ou zcat 
  * tail, cat, zcat peuvent prendre pluleurs fichiers en arguments
  * utiliser grep et egep pour inclure et exclure -v des paterns
  * utiliser cut pour améliorer la sortie
  

zcat ...  |egrep -v  "images/|.css|.js|favicon" | cut -d\  -f1,4,7,11

### Tail multiple files at same time
    
    sudo tail -f /var/log/php-scripts5.3.log /var/log/apache2/error.log app/logs/prod.log

### Apache IP count + nslookup
    
    zcat /var/log/apache2/access.log.2.gz |grep "13/Nov/2012:03"  | cut -d \   -f1 | sort | uniq -c | sort -n | tail | while read count ip; do n=`nslookup $ip | grep name`; echo "$count $n ($ip)"; done


# Process systems

## voir les process qui consomment le plus 
    
    ps -e -o pcpu,command --sort -%cpu | head
 
## voir les ips qui consomme le plus 
    
    netstat count netstat -anp | grep 'tcp\|udp' | awk '{print $5}' | cut -d: -f1 | sort | uniq -c | sort -n

## netstat open connexion
    
    netstat count netstat -tape | grep 'tcp\|udp' | awk '{print $4}'  | sort | uniq -c | sort -nr |head

## alertes syslog
    
    sudo tail -n 5000 /var/log/syslog | grep  --color "Max|max|error\|warning\|FATAL\|FAILED"




