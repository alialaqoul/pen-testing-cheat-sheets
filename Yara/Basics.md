
```Shell
yara myrule.yar somedirectory
```


```Yara_Template
rule helloworld_textfile_checker {
        Strings:
                $hello_world = "Hello World!"
                $txt_file = ".txt"
        condition:
                $hello_world and $txt_file 
}

```
