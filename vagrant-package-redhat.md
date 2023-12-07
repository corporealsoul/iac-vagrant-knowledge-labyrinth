### Vagrant custom box (Red Hat) ,

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
