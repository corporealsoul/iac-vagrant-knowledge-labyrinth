### Vagrant custom box (Red Hat) ,

**Prerequsites,**

`[anup@localhost ~]$ sestatus -v`

`[anup@localhost ~]$ sudo setenforce Enforcing`

`[anup@localhost ~]$ sudo restorecon -Rv /etc/selinux`

`[anup@localhost ~]$ sudo systemctl stop firewalld.service`

`[anup@localhost ~]$ sudo yum update kernel`

`[anup@localhost ~]$ sudo yum install -y kernel-devel`

`[anup@localhost ~]$ sudo dnf groupinstall "Development Tools" -y`

`[anup@localhost ~]$ sudo init 6`

`[anup@localhost ~]$ sudo subscription-manager repos --enable codeready-builder-for-rhel-9-$(arch)-rpms`

`[anup@localhost ~]$ sudo dnf install https://dl.fedoraproject.org/pub/epel/epel-release-latest-9.noarch.rpm -y`

`[anup@localhost ~]$ sudo yum update`

`[anup@localhost ~]$ sudo yum search dkms -y`

`[anup@localhost ~]$ sudo yum install dkms -y`

`[root@localhost ~]# ssh-keygen -t rsa -b 2048`



**Create Red Hat box,**

`PS C:\Users\uniqs> cd 'D:\Server Snaps\Vagrant Project\'`

`PS D:\Server Snaps\Vagrant Project\rhel-92-04-vagrantbox> vagrant package --base rhel-92-04-vagrantbox --output rhel-92-04-vagrantbox.box`

`PS D:\Server Snaps\Vagrant Project\rhel-92-04-vagrantbox> vagrant box add rhel-92-04-vagrantbox 'D:\Server Snaps\Vagrant Project\rhel-92-04-vagrantbox\rhel-92-04-vagrantbox.box'`

`PS D:\Server Snaps\Vagrant Project\rhel-92-04-vagrantbox> vagrant box list`

`PS D:\Server Snaps\Vagrant Project\rhel-92-04-vagrantbox> vagrant init rhel-92-04-vagrantbox`


    Vagrant.configure("2") do |config|
    
      config.vm.box = "rhel-92-04-vagrantbox"
    
      config.vm.provider "virtualbox" do |vb|
        vb.memory = "2048"
      end
    
      config.ssh.username = "root"
      config.ssh.password = " "
      config.ssh.insert_key = false
      config.ssh.forward_agent = true
    
      config.vm.network "public_network", ip: "192.168.56.4", :name => 'enp0s8', :adapter => 2
      
    end

**Control Red Hat box,**

`PS D:\Server Snaps\Vagrant Project\rhel-92-04-vagrantbox> vagrant up`

`PS D:\Server Snaps\Vagrant Project\rhel-92-04-vagrantbox> vagrant status`

`PS D:\Server Snaps\Vagrant Project\rhel-92-04-vagrantbox> vagrant ssh`

`PS D:\Server Snaps\Vagrant Project\rhel-92-04-vagrantbox> vagrant reload`

`PS D:\Server Snaps\Vagrant Project\rhel-92-04-vagrantbox> vagrant halt`

`PS D:\Server Snaps\Vagrant Project\rhel-92-04-vagrantbox> vagrant destroy`

<br>
