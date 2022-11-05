objdump dumps the .text section of the compliled binary

```Shell
objdump -d compiled_binary.ext
```

```Shell
objcopy -j .text -O binary compiled_binary.ext HEX.file
```
to read the HEX.file, you can use the following command
```Shell
xxd -i HEX.file
```


```C_program
#include <stdio.h>

int main(int argc, char **argv) {
    unsigned char message[] = {
		PASTE SHELLCODE HEX HERE
    };
    
    (*(void(*)())message)();
    return 0;
}
```

then compile using the following command (Linux)
```Shell
gcc -g -Wall -z execstack FILE.c -o OUTPUT_NAME
```


for Windows