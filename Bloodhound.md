
```Shell
sudo neo4j start
sudo bloodhound
```

To generate the loot file in Windows
```PowerShell
powershell -ep bypass
. .\SharpHound.ps1
Invoke-Bloodhound -CollectionMethod All -Domain domain.local -ZipFileName loot.zip
```

To use a Bloodhound Ingestor
```Shell
bloodhound-python -d domain.local -u user@domain.local -p pass -gc forest.domain.local -c all -ns 1.2.3.4 -v
```