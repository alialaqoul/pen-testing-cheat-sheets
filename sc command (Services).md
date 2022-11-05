Create a new service
```CMD
sc.exe create service_name binPath= "C:\windows\service_name.exe" start= auto
sc.exe start service_name
```

Configure an existing service
```CMD
sc.exe config service_name binPath= "C:\Windows\service_name.exe" start= auto obj= "LocalSystem"
```

