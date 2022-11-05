Example
```SHELL
./sigmac -t splunk -c ./config/generic/sysmon.yml ~/github/sigma/rules/windows/process_creation/proc_creation_win_susp_whoami.yml
```

Translate level high only
```Shell
tools/sigmac -I -t splunk -c splunk-windows -f 'level>=high' -r rules/windows/sysmon/
```

