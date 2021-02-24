# TimeMachine-ReadyNas-Fix
Fix backups to ReadyNAS Storage from Mac OS

1. Create a TimeMachine Backup from the ReadyNAS console
2. Cat the /etc/netatalk/timemachine.conf file to determine the location of the .timemachine directory
3. Copy the directory to the desired location for the share
4. Now edit the /etc/netatalk/timemachine.conf file
5. Finally, Update the target folder permissions
