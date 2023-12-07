### Vagrant custom box (Ubuntu) ,

**Prerequisetes,**

`anup@ubuntu-22point04point3-untouched:~$ sudo apt upgrade`

`anup@ubuntu-22point04point3-untouched:~$ sudo apt-get install build-essential`

`anup@ubuntu-22point04point3-untouched:~$ sudo apt install build-essential dkms linux-headers-generic`

`anup@ubuntu-22point04point3-untouched:~$ sudo rcvboxadd setup`

`anup@ubuntu-22point04point3-untouched:~$ sudo apt-get install libxt6`

`anup@ubuntu-22point04point3-untouched:~$ sudo apt-get install libxmu6`


**Create Ubuntu box,**

`PS D:\> cd 'D:\Server Snaps\Vagrant Boxes\ubuntu-22042-vagrantbox\'`

`PS D:\Server Snaps\Vagrant Boxes\ubuntu-22042-vagrantbox> vagrant package --base ubuntu-22042-vagrantbox --output ubuntu-22042-vagrantbox.box`

`PS D:\Server Snaps\Vagrant Boxes\ubuntu-22042-vagrantbox> vagrant box add ubuntu-22042-vagrantbox 'D:\Server Snaps\Vagrant Boxes\ubuntu-22042-vagrantbox\ubuntu-22042-vagrantbox.box'`

`PS D:\Server Snaps\Vagrant Boxes\ubuntu-22042-vagrantbox> vagrant box list`

`PS D:\Server Snaps\Vagrant Boxes\ubuntu-22042-vagrantbox> vagrant init `


    Vagrant.configure("2") do |config|
    
      config.vm.box = "ubuntu-22042-vagrantbox"
    
      config.vm.provider "virtualbox" do |vb|
        vb.memory = "2048"
      end
    
      config.ssh.username = "root"
      config.ssh.password = " "
      config.ssh.insert_key = false
      config.ssh.forward_agent = true
    
      config.vm.network "public_network", ip: "192.168.56.4", :name => 'enp0s8', :adapter => 2
      
    end

**Control Ubuntu box,**

`PS D:\Server Snaps\Vagrant Boxes\ubuntu-22042-vagrantbox> vagrant up`

`PS D:\Server Snaps\Vagrant Boxes\ubuntu-22042-vagrantbox> vagrant status`

`PS D:\Server Snaps\Vagrant Boxes\ubuntu-22042-vagrantbox> vagrant ssh`

`PS D:\Server Snaps\Vagrant Boxes\ubuntu-22042-vagrantbox> vagrant reload`

`PS D:\Server Snaps\Vagrant Boxes\ubuntu-22042-vagrantbox> vagrant halt`

`PS D:\Server Snaps\Vagrant Boxes\ubuntu-22042-vagrantbox> vagrant destroy`
