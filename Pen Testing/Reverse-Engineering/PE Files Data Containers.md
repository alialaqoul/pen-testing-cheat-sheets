
1.  **.text** stores the actual code of the program
2.  **.data** holds the initialized and defined variables
3.  **.bss** holds the uninitialized data (declared variables with no assigned values)
4.  **.rdata** contains the read-only data
5.  **.edata**: contains exportable objects and related table information
6.  **.idata** imported objects and related table information
7.  **.reloc** image relocation information
8.  **.rsrc** links external resources used by the program such as images, icons, embedded binaries, and manifest file, which has all information about program versions, authors, company, and copyright!


How the Windows loader reads an executable binary and runs it as a process.

1.  Header sections: DOS, Windows, and optional headers are parsed to provide information about the EXE file. For example,
-   The magic number starts with "MZ," which tells the loader that this is an EXE file.
-   File Signatures
-   Whether the file is compiled for x86 or x64 CPU architecture.
-   Creation timestamp. 
2.  Parsing the section table details, such as 
-   Number of Sections the file contains.
3.  Mapping the file contents into memory based on
-   The EntryPoint address and the offset of the ImageBase.   
-   RVA: Relative Virtual Address, Addresses related to Imagebase.  
4.  Imports, DLLs, and other objects are loaded into the memory.
5.  The EntryPoint address is located and the main execution function runs.