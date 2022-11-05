Add the following first to /etc/hosts
```HOSTS
1.2.3.4 DOMAIN.local
```

Usernames enumeration:
```Shell
kerbrute userenum --dc DOMAIN.local -d DOMAIN.local /usr/share/wordlists/userlist.txt
```

