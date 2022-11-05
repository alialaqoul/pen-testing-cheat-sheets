
```PowerShell
Set-NetFirewallProfile -Profile Domain, Public, Private -Enabled False
Get-NetFirewallProfile | Format-Table Name, Enabled
```

```PowerShell
Get-NetFirewallRule | select DisplayName, Enabled, Description
```

