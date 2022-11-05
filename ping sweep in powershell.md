
```powershell
2..254 | % {"172.25.170.$($_): $(Test-Connection -count 1 -comp 172.25.170.$($_) -quiet)"}
```
