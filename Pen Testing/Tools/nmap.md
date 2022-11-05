### Nmap

**To open the firewall port in linux**
```Shell
iptables -I INPUT -p tcp --dport <port> -j REJECT --reject-with tcp-reset
```


**For better results, use IPs instead of domain names.**

Ping sweep (map live hosts):

```bash

nmap -sn -oG nmap_ping_sweep_results.txt 192.168.8.0/24

nmap -sn -oG nmap_ping_sweep_results.txt -iL cidr.txt

```

Extract live hosts from the results:

```bash

grep -Po '(?<=Host\:\ )[^\s]+' nmap_ping_sweep_results.txt | sort -uf | tee -a ips.txt

```

TCP scan (all ports):

```fundamental

nmap -nv -sS -sV -sC -Pn -oN nmap_tcp_results.txt -p- 192.168.8.0/24

nmap -nv -sS -sV -sC -Pn -oN nmap_tcp_results.txt -p- -iL cidr.txt

```

\[Variation\] TCP scan (all ports):

```bash

mkdir nmap_tcp_results

for ip in $(cat ips.txt); do nmap -nv -sS -sV -sC -Pn -oN nmap_tcp_results/nmap_tcp_results_${ip//./_}.txt -p- "${ip}"; done

```

UDP scan (only important ports):

```fundamental

nmap -nv -sU -sV -sC -Pn -oN nmap_udp_results.txt -p 53,67,68,69,88,123,135,137,138,139,161,162,389,445,500,514,631,1900,4500 192.168.8.0/24

nmap -nv -sU -sV -sC -Pn -oN nmap_udp_results.txt -p 53,67,68,69,88,123,135,137,138,139,161,162,389,445,500,514,631,1900,4500 -iL cidr.txt

```

\[Variation\] UDP scan (only important ports):

```bash

mkdir nmap_udp_results

for ip in $(cat ips.txt); do nmap -nv -sU -sV -sC -Pn -oN nmap_udp_results/nmap_udp_results_${ip//./_}.txt -p 53,67,68,69,88,123,135,137,138,139,161,162,389,445,500,514,631,1900,4500 "${subdomain}"; done

```

