**Guest Addition,**

`[anup@localhost ~]$ sudo mount /dev/cdrom /mnt`

`[anup@localhost ~]$ ls -ltr /mnt`

`[anup@localhost ~]$ sudo /mnt/VBoxLinuxAdditions.run`

`[anup@localhost ~]$ sudo /sbin/rcvboxadd quicksetup all`

`[anup@localhost ~]$ VBoxClient --version`

`[anup@localhost ~]$ sudo umount /mnt`

`[anup@localhost ~]$ sudo reboot now`

`[anup@localhost ~]$ lsmod | grep vbox`

`[anup@localhost ~]$ lsmod | grep vboxguest`

`[anup@localhost ~]$ VBoxClient --version`

`[anup@localhost ~]$ tail /var/log/vboxadd-setup.log`


**Mount the VirtualBox Guest Additions ISO:** mount /dev/cdrom /mnt

`[root@rhel-92-04-vagrantbox ~]# mount /dev/cdrom /mnt`

<br>

**Run the installer:** sh /mnt/VBoxLinuxAdditions.run

`[root@rhel-92-04-vagrantbox ~]# sh /mnt/VBoxLinuxAdditions.run`

`[root@rhel-92-04-vagrantbox ~]# /sbin/rcvboxadd quicksetup all`

`[root@rhel-92-04-vagrantbox ~]# VBoxClient --version`


<br>

**Umount the ISO:** umount /mnt

`[root@rhel-92-04-vagrantbox ~]# umount /mnt`

<br>

**Restart,**

`[root@rhel-92-04-vagrantbox ~]# sudo reboot now`

<br>

**Check installation,**

`[root@rhel-92-04-vagrantbox ~]# lsmod | grep vboxguest`

`[root@rhel-92-04-vagrantbox ~]# VBoxClient --version`

<br> 

**Setup environment variable,**

`C:\Program Files\Oracle\VirtualBox`

`PS C:\Users\uniqs> VBoxManage --version`

`PS D:\Server Snaps\OVA Project> VBoxManage export rhel-92-108 -o rhel-92-108.ova`
