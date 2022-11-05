
```Shell
zip2john zipfile.zip > zip_hash.txt
```

```Shell
john --wordlist=/usr/share/wordlists/rockyou.txt zip_hash.txt
```
