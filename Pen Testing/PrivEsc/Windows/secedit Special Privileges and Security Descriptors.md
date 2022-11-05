To export the config in .inf format
```CMD
secedit /export /cfg config.inf
```

To import the .inf and convert it to .sdb
```CMD
secedit /import /cfg config.inf /db config.sdb
secedit /configure /db config.sdb /cfg config.inf
```

**SeBackupPrivilege and SeRestorePrivilege are highly privileged**




To open/verify the configuration window for WinRM's security descriptor
```powershell
Set-PSSessionConfiguration -Name Microsoft.PowerShell -showSecurityDescriptorUI
```
