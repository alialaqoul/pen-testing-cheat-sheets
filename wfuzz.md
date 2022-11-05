wfuzz with encoder
```Command
wfuzz -z file --zP fn=/usr/share/wordlists/seclists/Fuzzing/LFI/LFI-LFISuite-pathtotest-huge.txt,encoder=base64 -u https://vidm.stc.com.sa/SAAS/horizon/js
/util.autofocus.97b2f2aa2244bde7495522a6eb8cf176.js?v=FUZZ --hw 168

```

Another simple encoder way
```Command
wfuzz -z file,wordlist/general/common.txt,md5 http://testphp.vulnweb.com/FUZZ
```

**Available encoders:

wfuzz -e encoders

  Category      | Name              | Summary
  hashes        | base64            | Encodes the given string using base64
  url           | doble_nibble_hex  | Replaces ALL characters in string using the %%dd%dd escape
  url_safe, url | double_urlencode  | Applies a double encode to special characters in string using the %25xx escape.
                |                   | Letters, digits, and the characters '_.-' are never quoted.
  url           | first_nibble_hex  | Replaces ALL characters in string using the %%dd? escape
  default       | hexlify           | Every byte of data is converted into the corresponding 2-digit hex representatio
                |                   | n.
  html          | html_decimal      | Replaces ALL characters in string using the &#dd; escape
  html          | html_escape       | Convert the characters &<>" in string to HTML-safe sequences.
  html          | html_hexadecimal  | Replaces ALL characters in string using the &#xx; escape
  hashes        | md5               | Applies a md5 hash to the given string
  db            | mssql_char        | Converts ALL characters to MsSQL's char(xx)
  db            | mysql_char        | Converts ALL characters to MySQL's char(xx)
  default       | none              | Returns string without changes
  db            | oracle_char       | Converts ALL characters to Oracle's chr(xx)
  default       | random_upper      | Replaces random characters in string with its capitals letters
  url           | second_nibble_hex | Replaces ALL characters in string using the %?%dd escape
  hashes        | sha1              | Applies a sha1 hash to the given string
  hashes        | sha256            | Applies a sha256 hash to the given string
  hashes        | sha512            | Applies a sha512 hash to the given string
  url           | uri_double_hex    | Encodes ALL charachers using the %25xx escape.
  url           | uri_hex           | Encodes ALL charachers using the %xx escape.
  url           | uri_triple_hex    | Encodes ALL charachers using the %25%xx%xx escape.
  url           | uri_unicode       | Replaces ALL characters in string using the %u00xx escape
  url_safe, url | urlencode         | Replace special characters in string using the %xx escape. Letters, digits, and
                |                   | the characters '_.-' are never quoted.
  url           | utf8              | Replaces ALL characters in string using the \u00xx escape
  url           | utf8_binary       | Replaces ALL characters in string using the \uxx escape

