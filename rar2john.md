
```Shell
rar2john rarfile.rar > rar_hash.txt
```

```Shell
john --wordlist=/usr/share/wordlists/rockyou.txt rar_hash.txt
```
