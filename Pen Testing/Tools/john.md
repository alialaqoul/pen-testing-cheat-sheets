
```Shell
john --format=[format] --wordlist=[path to wordlist] [path to file]
```


Generate a password list from a single password list
```Shell
john --wordlist=/tmp/single-password-list.txt --rules=best64 --stdout
```

Generate a new John the ripper rule
```Shell
sudo vi /etc/john/john.conf [List.Rules:THM-Password-Attacks] Az"[0-9]" ^[!@#$]
```

Az represents a single word from the original wordlist/dictionary using -p.

"[0-9]" append a single digit (from 0 to 9) to the end of the word. For two digits, we can add "[0-9][0-9]"  and so on.  

^[!@#$] add a special character at the beginning of each word. ^ means the beginning of the line/word. Note, changing ^ to $ will append the special characters to the end of the line/word.


To list all John the ripper rules
```Shell
cat /etc/john/john.conf|grep "List.Rules:" | cut -d"." -f3 | cut -d":" -f2 | cut -d"]" -f1 | awk NF
```

o1
o2
i1
i2
o1
i1
o2
i2
best64
d3ad0ne
dive
InsidePro
T0XlC
rockyou-30000
specific
ShiftToggle
Split
Single
Extra
OldOffice
Single-Extra
Wordlist
ShiftToggle
Multiword
best64 --> popular
UnicodeSubstitution
Jumbo
KoreLogic --> e.g. a --> @
T9

