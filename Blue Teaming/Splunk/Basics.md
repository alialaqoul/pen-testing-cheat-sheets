
If you want to land into the Search app upon login automatically, you can do so by editing the `user-prefs.conf` file. 

Change default_namespace to search
-   Windows: `C:\Program Files\Splunk\etc\apps\user-prefs\default\user-prefs.conf`
-   Linux:`/opt/splunk/etc/apps/user-pref/default/user-prefs.conf`



If you wish to remove an app (or an add-on), you can do so via the command-lin
```CMD
C:\Program Files\Splunk\bin>splunk.exe remove app app-name -auth splunk-username:splunk-password
```

