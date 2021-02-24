

root@KOIOS:/Store# vi /etc/netatalk/timemachine.conf
root@KOIOS:/Store# systemctl restart netatalk
root@KOIOS:/Store# ls -la
total 8
drwxr-xr-x   1 root  root   180 Jul 27  2020 .
drwxr-xr-x  28 root  root  4096 Feb 23 22:59 ..
drwxrwxr-x   1 admin admin  268 Feb 21 22:03 .apps
drwxrwxrwx+  1 guest guest  122 Nov 25 12:23 Backups
drwx------+  1 admin admin 2060 Feb  9 15:18 GoogleDrive
drwxr-xr-x   1 admin admin   38 Feb 24 00:04 home
drwxrwxrwx+  1 guest guest  592 Dec  2 21:03 MaxtorBKUP
drwxrwxrwx+  1 guest guest   90 May  3  2020 Music
d---------+  1 guest guest  448 Sep 23 12:19 Personal
drwxr-xr-x   1 root  root     0 Jul 27  2020 .purge
drwxrwxrwx+  1 guest guest    0 Oct 26  2013 readydrop
drwxr-xr-x   1 root  root   100 Jul 27  2020 ._share
drwxr-xr-x   1 root  root    16 Feb 24 00:34 .timemachine
drwxr-xr-x   1 root  root     0 Oct 26  2013 .vault
root@KOIOS:/Store# vi /etc/netatalk/timemachine.conf
root@KOIOS:/Store# cd /WD14Disk3/StephTimeMachine/
root@KOIOS:/WD14Disk3/StephTimeMachine# ls
root@KOIOS:/WD14Disk3/StephTimeMachine# ls -la
total 40
drwxrwxrwx+ 1 guest guest   78 Feb 24 00:52 .
drwxr-xr-x  1 root  root   234 Feb 23 22:36 ..
drwxr-xr-x+ 1 root  root    70 Feb 24 00:49 .AppleDB
-rw-rwxrw-+ 1 Steph admin 6148 Feb 24 00:02 .DS_Store
drwxr-xr-x+ 1 root  root    16 Feb 24 00:52 .timemachine
root@KOIOS:/WD14Disk3/StephTimeMachine# cd .timemachine/
root@KOIOS:/WD14Disk3/StephTimeMachine/.timemachine# ls
ReadyNAS
root@KOIOS:/WD14Disk3/StephTimeMachine/.timemachine# systemctl status netatalk
● netatalk.service - Netatalk AFP fileserver for Macintosh clients
   Loaded: loaded (/lib/systemd/system/netatalk.service; enabled; vendor preset: disabled)
   Active: active (running) since Wed 2021-02-24 01:02:56 WET; 3min 20s ago
     Docs: man:afp.conf(5)
           man:netatalk(8)
           man:afpd(8)
           man:cnid_metad(8)
           man:cnid_dbd(8)
           http://netatalk.sourceforge.net/
  Process: 26286 ExecReload=/bin/kill -HUP $MAINPID (code=exited, status=0/SUCCESS)
  Process: 28000 ExecStart=/usr/sbin/netatalk (code=exited, status=0/SUCCESS)
 Main PID: 28004 (netatalk)
   CGroup: /system.slice/netatalk.service
           ├─28004 /usr/sbin/netatalk
           ├─28005 /usr/sbin/afpd -d -F /etc/netatalk/afp.conf
           ├─28006 /usr/sbin/cnid_metad -d -F /etc/netatalk/afp.conf
           └─28251 /usr/sbin/cnid_dbd -F /etc/netatalk/afp.conf -p /Store/.timemachine/ReadyNAS -t 8 -l 6 -u ReadyNAS

Feb 24 01:03:47 KOIOS afpd[28239]: dsi_stream_read: len:0, unexpected EOF
Feb 24 01:03:47 KOIOS afpd[28239]: afp_over_dsi: client logged out, terminating DSI session
Feb 24 01:04:01 KOIOS afpd[28249]: pam_unix(netatalk:session): session opened for user ReadyNAS by (uid=0)
Feb 24 01:04:01 KOIOS afpd[28249]: pam_mkhomedir(netatalk:session): conversation failed
Feb 24 01:04:01 KOIOS afpd[28249]: Login by ReadyNAS (AFP3.4)
Feb 24 01:04:04 KOIOS afpd[28249]: AFP logout by ReadyNAS
Feb 24 01:04:04 KOIOS afpd[28249]: pam_unix(netatalk:session): session closed for user ReadyNAS
Feb 24 01:04:04 KOIOS afpd[28249]: PAM audit_log_acct_message() failed: Operation not permitted
Feb 24 01:04:04 KOIOS afpd[28249]: AFP statistics: 1.75 KB read, 1.36 KB written
Feb 24 01:04:04 KOIOS afpd[28249]: done
root@KOIOS:/WD14Disk3/StephTimeMachine/.timemachine# cat /etc/netatalk/afp.conf
# Do not edit.
[Global]
 uam list = uams_dhx.so uams_dhx2.so uams_guest.so
 save password = no
 unix charset = UTF8
 mac charset = MAC_ROMAN
 guest account = guest
 start dbus = no
 start tracker = no

#[Homes]
# basedir regex = /home.*/
#
include = /etc/frontview/netatalk/Shares.conf
include = /run/usb/netatalk/Shares.conf
include = /etc/netatalk/timemachine.conf
root@KOIOS:/WD14Disk3/StephTimeMachine/.timemachine# cat /run/usb/netatalk/Shares.conf 
root@KOIOS:/WD14Disk3/StephTimeMachine/.timemachine# vi /etc/netatalk/timemachine.conf
root@KOIOS:/WD14Disk3/StephTimeMachine/.timemachine# systemctl restart afpd
Failed to restart afpd.service: Unit afpd.service not found.
root@KOIOS:/WD14Disk3/StephTimeMachine/.timemachine# systemctl restart netatalk
root@KOIOS:/WD14Disk3/StephTimeMachine/.timemachine# cd ..
root@KOIOS:/WD14Disk3/StephTimeMachine# ls -la
total 40
drwxrwxrwx+ 1 guest guest   78 Feb 24 00:52 .
drwxr-xr-x  1 root  root   234 Feb 23 22:36 ..
drwxr-xr-x+ 1 root  root    70 Feb 24 00:49 .AppleDB
-rw-rwxrw-+ 1 Steph admin 6148 Feb 24 00:02 .DS_Store
drwxr-xr-x+ 1 root  root    16 Feb 24 00:52 .timemachine
root@KOIOS:/WD14Disk3/StephTimeMachine# getacl .timemachine/
-bash: getacl: command not found
root@KOIOS:/WD14Disk3/StephTimeMachine# getfacl .timemachine/
# file: .timemachine/
# owner: root
# group: root
user::rwx
user:admin:rwx			#effective:r-x
user:guest:rwx			#effective:r-x
group::rwx			#effective:r-x
group:admin:rwx			#effective:r-x
group:guest:rwx			#effective:r-x
mask::r-x
other::r-x
default:user::rwx
default:user:admin:rwx
default:user:guest:rwx
default:group::rwx
default:group:admin:rwx
default:group:guest:rwx
default:mask::rwx
default:other::rwx

root@KOIOS:/WD14Disk3/StephTimeMachine# getfacl /Store/.timemachine/
getfacl: Removing leading '/' from absolute path names
# file: Store/.timemachine/
# owner: root
# group: root
user::rwx
group::r-x
other::r-x

root@KOIOS:/WD14Disk3/StephTimeMachine# chmod 755 .timemachine/
root@KOIOS:/WD14Disk3/StephTimeMachine# getfacl .timemachine/
# file: .timemachine/
# owner: root
# group: root
user::rwx
user:admin:rwx			#effective:r-x
user:guest:rwx			#effective:r-x
group::rwx			#effective:r-x
group:admin:rwx			#effective:r-x
group:guest:rwx			#effective:r-x
mask::r-x
other::r-x
default:user::rwx
default:user:admin:rwx
default:user:guest:rwx
default:group::rwx
default:group:admin:rwx
default:group:guest:rwx
default:mask::rwx
default:other::rwx

root@KOIOS:/WD14Disk3/StephTimeMachine# chown root:root .timemachine/
root@KOIOS:/WD14Disk3/StephTimeMachine# getfacl .timemachine/
# file: .timemachine/
# owner: root
# group: root
user::rwx
user:admin:rwx			#effective:r-x
user:guest:rwx			#effective:r-x
group::rwx			#effective:r-x
group:admin:rwx			#effective:r-x
group:guest:rwx			#effective:r-x
mask::r-x
other::r-x
default:user::rwx
default:user:admin:rwx
default:user:guest:rwx
default:group::rwx
default:group:admin:rwx
default:group:guest:rwx
default:mask::rwx
default:other::rwx

root@KOIOS:/WD14Disk3/StephTimeMachine# setfacl -b .timemachine/
root@KOIOS:/WD14Disk3/StephTimeMachine# getfacl .timemachine/
# file: .timemachine/
# owner: root
# group: root
user::rwx
group::r-x
other::r-x

root@KOIOS:/WD14Disk3/StephTimeMachine# cd .timemachine/
root@KOIOS:/WD14Disk3/StephTimeMachine/.timemachine# ls
ReadyNAS
root@KOIOS:/WD14Disk3/StephTimeMachine/.timemachine# getfacl ReadyNAS/
# file: ReadyNAS/
# owner: root
# group: root
user::rwx
user:admin:rwx			#effective:r-x
user:guest:rwx			#effective:r-x
group::rwx			#effective:r-x
group:admin:rwx			#effective:r-x
group:guest:rwx			#effective:r-x
mask::r-x
other::r-x
default:user::rwx
default:user:admin:rwx
default:user:guest:rwx
default:group::rwx
default:group:admin:rwx
default:group:guest:rwx
default:mask::rwx
default:other::rwx

root@KOIOS:/WD14Disk3/StephTimeMachine/.timemachine# getfacl /Store/.timemachine/ReadyNAS/
getfacl: Removing leading '/' from absolute path names
# file: Store/.timemachine/ReadyNAS/
# owner: ReadyNAS
# group: 96
user::rwx
group::r-x
other::r-x

root@KOIOS:/WD14Disk3/StephTimeMachine/.timemachine# setfacl -b ReadyNAS/
root@KOIOS:/WD14Disk3/StephTimeMachine/.timemachine# getfacl ReadyNAS/
# file: ReadyNAS/
# owner: root
# group: root
user::rwx
group::r-x
other::r-x

root@KOIOS:/WD14Disk3/StephTimeMachine/.timemachine# chown Steph:Steph ReadyNAS/
chown: invalid group: ‘Steph:Steph’
root@KOIOS:/WD14Disk3/StephTimeMachine/.timemachine# chown Steph ReadyNAS/
root@KOIOS:/WD14Disk3/StephTimeMachine/.timemachine# chown Steph:Steph ReadyNAS/
chown: invalid group: ‘Steph:Steph’
root@KOIOS:/WD14Disk3/StephTimeMachine/.timemachine# getfacl ReadyNAS/
# file: ReadyNAS/
# owner: Steph
# group: root
user::rwx
group::r-x
other::r-x
