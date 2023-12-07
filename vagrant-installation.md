### Installation,

**Download and install,** https://www.vagrantup.com/

`PS D:\Server Snaps\The Architect> vagrant plugin install vagrant-vbguest`

`PS D:\Server Snaps\The Architect> vagrant vbguest --status`

<br>

`PS D:\Server Snaps\Vagrant Project> vagrant --version`

`PS D:\Server Snaps\Vagrant Project> vagrant status`

### Plugins,

`PS D:\Server Snaps\Vagrant Project> vagrant plugin list`

`PS D:\Server Snaps\Vagrant Project> vagrant plugin install vagrant-vbguest`

`PS D:\Server Snaps\Vagrant Project> vagrant plugin list`

`PS D:\Server Snaps\Vagrant Project> vagrant vbguest --status`

`PS D:\Server Snaps\Vagrant Project> vagrant plugin update `

`PS D:\Server Snaps\Vagrant Project> vagrant plugin update vagrant-vbguest`

`PS D:\Server Snaps\Vagrant Project> vagrant plugin uninstall vagrant-vbguest`

### Vagrant box,

**Vagrant boxes,** https://app.vagrantup.com/boxes/search

`PS D:\Server Snaps\Vagrant Project> vagrant box list`

`PS D:\Server Snaps\Vagrant Project> vagrant box add ubuntu/focal64`

    Location, C:\Users\uniqs\.vagrant.d

`PS D:\Server Snaps\Vagrant Project> vagrant box list`

`PS D:\Server Snaps\Vagrant Project> vagrant box remove ubuntu/focal64`


### Vagrant init,

`PS D:\Server Snaps\Vagrant Project\ubuntu-focal-64> vagrant init ubuntu/focal64`

`PS D:\Server Snaps\Vagrant Project\ubuntu-bionic-64> vagrant init ubuntu/bionic64`

`PS D:\Server Snaps\Vagrant Project\ubuntu-focal-64> ls`

`PS D:\Server Snaps\Vagrant Project\ubuntu-focal-64> vagrant up`

`PS D:\Server Snaps\Vagrant Project\ubuntu-focal-64> vagrant status`

`PS D:\Server Snaps\Vagrant Project\ubuntu-focal-64> vagrant box outdated`

`PS D:\Server Snaps\Vagrant Project\ubuntu-focal-64> vagrant box update`


### Vagrant ssh, halt, destroy

`PS D:\Server Snaps\Vagrant Project\ubuntu-focal-64> vagrant ssh`

`vagrant@ubuntu-focal:~$ exit`

`PS D:\Server Snaps\Vagrant Project\ubuntu-focal-64> vagrant reload`

`PS D:\Server Snaps\Vagrant Project\ubuntu-focal-64> vagrant halt`

`PS D:\Server Snaps\Vagrant Project\ubuntu-focal-64> vagrant destroy`

`PS D:\Server Snaps\The Architect> vagrant vbguest --auto-reboot`

`PS D:\Server Snaps\The Architect> vagrant reload --provision`

### Snapshot,

`PS D:\Server Snaps\Vagrant Project\rhel-92-vagrantbox> vagrant snapshot list           `

`PS D:\Server Snaps\Vagrant Project\rhel-92-vagrantbox> vagrant snapshot push controllerinfra`

`PS D:\Server Snaps\Vagrant Project\rhel-92-vagrantbox> vagrant snapshot list`

`PS D:\Server Snaps\Vagrant Project\rhel-92-vagrantbox> vagrant snapshot restore push_1689829970_6089`

`PS D:\Server Snaps\Vagrant Project\rhel-92-vagrantbox> vagrant snapshot delete push_1689829970_6089`

https://developer.hashicorp.com/vagrant/docs/cli/snapshot

`PS D:\Server Snaps\The Architect> vagrant snapshot save '26 July 2023 23:18:47'`

`PS D:\Server Snaps\The Architect> vagrant snapshot restore '26 July 2023 23:18:47'`

`PS D:\Server Snaps\The Architect> vagrant snapshot delete '26 July 2023 23:18:47'`

<br>
