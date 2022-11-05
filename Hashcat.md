### Hashcat

Brute force MD5 hashes:

```fundamental

hashcat -m 0 -a 3 --session=cracking --force --status -O -o hashcat_results.txt hashes.txt

```

Brute force NetNTLMv1 hashes:

```fundamental

hashcat -m 5500 -a 3 --session=cracking --force --status -O -o hashcat_results.txt hashes.txt

```

Use `--session=<session_name>` so that you can continue your cracking progress later on with `--restore`.

Continue cracking progress:

```fundamental

hashcat --session=cracking --restore

```

Generate a dictionary
```Shell
hashcat -a 3 ?d?d?d?d --stdout
```



| Option | Description |

| --- | --- |

| -m | Hash-type, see references below |

| -a | Attack-mode, see references below |

| --force | Ignore warnings |

| --runtime | Abort session after X seconds of runtime |

| --status | Enable automatic update of the status screen |

| -o | Define outfile for recovered hash |

| --show | Show cracked passwords found in potfile |

| --session | Define specific session name |

| --restore | Restore session from --session |

| --restore-file-path | Specific path to restore file |

| -O | Enable optimized kernels (limits password length) |

| -1 | User-defined charset ?1 |

| -2 | User-defined charset ?2 |

| -3 | User-defined charset ?3 |

| -4 | User-defined charset ?4 |

**When specifying a user-defined charset, escape `?` with another `?` (i.e. use `??` instead of `\?`).**

| Hash Type | Description |

| --- | --- |

| 0 | MD5 |

| 100 | SHA1 |

| 1400 | SHA256 |

| 1700 | SHA512 |

| 200 | MySQL323 |

| 300 | MySQL4.1/MySQL5 |

| 1000 | NTLM |

| 5500 | NetNTLMv1-VANILLA / NetNTLMv1-ESS |

| 5600 | NetNTLMv2 |

| 2500 | WPA/WPA2 |

| 16800 | WPA-PMKID-PBKDF2 |

For more hash types read the manual.

| Attack Mode | Name |

| --- | --- |

| 0 | Straight |

| 1 | Combination |

| 2 | Toggle Case |

| 3 | Brute Force |

| 4 | Permutation |

| 5 | Table Lookup |

| 8 | Prince |

| Charset | Description |

| --- | --- |

| \?l | abcdefghijklmnopqrstuvwxyz |

| \?u | ABCDEFGHIJKLMNOPQRSTUVWXYZ |

| \?d | 0123456789 |

| \?s | \!\"\#\$\%\&\'\(\)\*\+\,\-\.\/\:\;\<\=\>\?\@\[\]\^\_\`\{\|\}\~ |

| \?a | \?l\?u\?d\?s |

| \?b | 0x00 - 0xff |

Dictionary attack:

```fundamental

hashcat -m 100 -a 0 --session=cracking --force --status -O B1B3773A05C0ED0176787A4F1574FF0075F7521E rockyou.txt

hashcat -m 5600 -a 0 --session=cracking --force --status -O -o hashcat_results.txt hashes.txt rockyou.txt

```

You can find `rockyou.txt` wordlist in [SecLists](#wordlists).

Brute force a hash with a specified placeholder:

```fundamental

hashcat -m 0 -a 3 --session=cracking --force --status -O cc158fa2f16206c8bd2c750002536211 -1 ?l?u -2 ?d?s ?1?l?l?l?l?l?2?2

hashcat -m 0 -a 3 --session=cracking --force --status -O 85fb9a30572c42b19f36d215722e1780 -1 \!\"\#\$\%\&\/\(\)\=??\* -2 ?d?1 ?u?l?l?l?l?2?2?2

```