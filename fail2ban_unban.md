
## Fail2Ban Unban

http://ubuntuforums.org/showthread.php?t=328800

steps to unban banned user:

     sudo iptables -L

look at the Chain fail2ban-ssh  
notice the ip address to unban and count at which line number this is.  

e.g.: 
    
    Chain fail2ban-ssh (1 references)
    target prot opt source destination
    DROP 0 -- 61.236.117.xxx anywhere
    DROP 0 -- 61.236.117.yyy anywhere
    RETURN 0 -- anywhere anywhere

execute the following command:

    iptables -D fail2ban-ssh <linenum>

if you want to unban user 61.236.117.yyy use:

    iptables -D fail2ban-ssh 2
