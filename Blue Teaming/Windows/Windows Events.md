The log files with the .evtx file extension typically reside in ```
```PATH
C:\Windows\System32\winevt\Logs
```


Here are 3 main ways of accessing these event logs within a Windows system:

1.  **Event Viewer** (GUI-based application)
2.  **Wevtutil.exe** (command-line tool)
3.  **Get-WinEvent** (PowerShell cmdlet)

![[Types of Windows Events.png]]


**wevtutil**

```CMD
wevtutil qe Application /c:3 /rd:true /f:text
```
**/rd** Event read direction
**/c** Maximum number of events to read



**Get-WinEvent**

```PowerShell
Get-WinEvent -LogName Application | Where-Object { $_.ProviderName -Match 'WLMS' }
Get-WinEvent -LogName Application | Where-Object { $_.ID -eq 100 }
Get-WinEvent -LogName Application -FilterXPath '*/System/EventID=100'
Get-WinEvent -LogName Application -FilterXPath '*/System/Provider[@Name="WLMS"]'
Get-WinEvent -LogName Application -FilterXPath '*/System/EventID=101 and */System/Provider[@Name="WLMS"]'
Get-WinEvent -LogName Application -FilterXPath '*/System/Provider[@Name="WLMS"] and */System/TimeCreated[@SystemTime="2020–12–15T01:09:08.940277500Z"]'
```
**-MaxEvents** specify the number of events to display



![[Get-WinEvent-Keys.png]]



**PoweShell ISE**
```PowerShelISE
Get-WinEvent -FilterHashtable @{
    LogName ='Application'
    ProviderName='MsiInstaller'
    ID=11707
}
```

