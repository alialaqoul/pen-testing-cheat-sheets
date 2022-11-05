
**Detecting Open Network Ports**
```PowerShell
Get-WinEvent -Path file.evtx -FilterXPath '*/System/EventID=3 and */EventData/Data[@Name="DestinationPort"] and */EventData/Data=4444'
```



**Detecting LSASS Behavior**
```PowerShell
Get-WinEvent -Path <Path to Log> -FilterXPath '*/System/EventID=10 and */EventData/Data[@Name="TargetImage"] and */EventData/Data="C:\Windows\system32\lsass.exe"'
```


**Detecting Registry Key Persistence**
HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Run\Persistence



**Detecting Startup Persistence**
Event ID 11 "File Created" & "\Startup\" or "\Start Menu"

**Detecting Alternate Data Streams**
Event ID 15 will hash and log any NTFS Streams that are included within the Sysmon configuration file. This will allow us to hunt for malware that evades detections using ADS. To aid in hunting ADS we will be using the SwiftOnSecurity Sysmon configuration file. The code snippet below will hunt for files in the `Temp` and `Startup` folder as well as `.hta` and `.bat` extension.


**Detecting Remote Threads**
