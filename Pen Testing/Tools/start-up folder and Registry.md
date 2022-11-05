
```DIR
C:\ProgramData\Microsoft\Windows\Start Menu\Programs\StartUp
```

```CMD
copy file.exe "C:\ProgramData\Microsoft\Windows\Start Menu\Programs\StartUp\"
```

```registry
move file.exe C:\Windows
HKCU\Software\Microsoft\Windows\CurrentVersion\Run
HKCU\Software\Microsoft\Windows\CurrentVersion\RunOnce

and then create a new registry key inside Run or RunOnce with any name. The key type is REG_EXPAND_SZ and the data is the full path of the executable
```




