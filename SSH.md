
If you get an error saying `Unable to negotiate with <IP> port 22: no matching how to key type found. Their offer: ssh-rsa, ssh-dss` this is because OpenSSH have deprecated ssh-rsa. Add 
```shell
-oHostKeyAlgorithms=+ssh-rsa
```

```Shell
chmod 600 id_rsa
```

```Shel
ssh -i id_rsa -oPubkeyAcceptedKeyTypes=+ssh-rsa -oHostKeyAlgorithms=+ssh-rsa user@1.2.3.4
```
