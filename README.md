# TimeMachine-ReadyNas-Fix
Fix backups to ReadyNAS Storage from Mac OS

Create a TimeMachine Backup from the ReadyNAS console
Cat the /etc/netatalk/timemachine.conf file to determine the location of the .timemachine directory
Copy the directory to the desired location for the share
Now edit the /etc/netatalk/timemachine.conf file
Finally, Update the target folder permissions
