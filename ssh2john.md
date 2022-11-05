
```Shell
ssh2john id_rsa > id_rsa_hash.txt
```

```Shell
john --wordlist=/usr/share/wordlists/rockyou.txt id_rsa_hash.txt
```

```DIR
~/.ssh/id_rsa
```
