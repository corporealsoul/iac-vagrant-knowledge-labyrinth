### Cluster setup,

`PS D:\Server Snaps\Vagrant Project\rhel-92-vagrantbox> vagrant package --base rhel-92-04-vagrantbox --output rhel-92-vagrantbox.box`

`PS D:\Server Snaps\Vagrant Project\rhel-92-vagrantbox> vagrant box list`

`PS D:\Server Snaps\Vagrant Project\rhel-92-vagrantbox> vagrant box add rhel-92-vagrantbox 'D:\Server Snaps\Vagrant Project\rhel-92-vagrantbox\rhel-92-vagrantbox.box'`

`PS D:\Server Snaps\Vagrant Project\rhel-92-vagrantbox> vagrant box list`

`PS D:\Server Snaps\Vagrant Project\rhel-92-vagrantbox> vagrant init rhel-92-vagrantbox`


    # -*- mode: ruby -*-
    # vi: set ft=ruby :
    
    # All Vagrant configuration is done below. The "2" in Vagrant.configure
    # configures the configuration version (we support older styles for
    # backwards compatibility). Please don't change it unless you know what
    # you're doing.
    
    Vagrant.configure("2") do |config|
    
      config.vm.box = "rhel-92-04-vagrantbox"
    
      config.vm.provider "virtualbox" do |vb|
        vb.memory = 4096
        vb.cpus = 2
      end
    
    
    
    # Controller
      config.vm.define "controllerinfra" do |controllerinfra|
        controllerinfra.vm.hostname = "controllerinfra"
        controllerinfra.vm.network "public_network", ip: "192.168.56.5", :name => 'enp0s8', :adapter => 2
        controllerinfra.vm.provider "virtualbox" do |vb|
          vb.name = "controllerinfra"
        end
        controllerinfra.vm.provision "shell", inline: <<-SHELL
          
          # Disable firewall and SELinux
          sudo systemctl stop firewalld.service
          sudo systemctl disable firewalld.service
    
          setenforce 0
    
          # Install required softwares
          dnf install -y epel-release
          dnf update -y
          dnf install htop -y
          dnf install multitail -y 
    
          # Manage DNS
          echo "192.168.56.5	controllerinfra" | sudo tee -a /etc/hosts
          echo "192.168.56.6	workerdev" | sudo tee -a /etc/hosts
          echo "192.168.56.7	workerdeploy" | sudo tee -a /etc/hosts
          echo "192.168.56.8	workermonitor" | sudo tee -a /etc/hosts
    
          # Create a new user
          sudo useradd -m -s /bin/bash anup
          echo 'anup: ' | sudo chpasswd
          sudo usermod -aG wheel anup
    
          # Install Ansible
          sudo dnf install -y ansible
    
          # Authentication
          ssh-keygen
    
          ssh-copy-id root@192.168.56.5
          ssh-copy-id root@192.168.56.6
          ssh-copy-id root@192.168.56.7
          ssh-copy-id root@192.168.56.8
    
          # Write the Ansible inventory content to /etc/ansible/hosts
    
          sudo tee /etc/ansible/hosts > /dev/null <<EOF
    
    [controllerinfra]
    192.168.56.5  ansible_user=root
    
    [workerdev]
    192.168.56.7  ansible_user=root
    
    [workerdeploy]
    192.168.56.7  ansible_user=root
    
    [workermonitor]
    192.168.56.8  ansible_user=root
    EOF
    
          # visudo
          echo "anup ALL=(ALL) NOPASSWD:ALL" | sudo tee -a /etc/sudoers
    
      SHELL
      end
    
    
    
    # Worker Developement Machine
      config.vm.define "workerdev" do |workerdev|
        workerdev.vm.hostname = "workerdev"
        workerdev.vm.network "public_network", ip: "192.168.56.6", :name => 'enp0s8', :adapter => 2
        workerdev.vm.provider "virtualbox" do |vb|
          vb.name = "workerdev"
        end
        workerdev.vm.provision "shell", inline: <<-SHELL
          # Install required softwares
          dnf install -y epel-release
          dnf update -y
          dnf install htop -y
          dnf install multitail -y
    
          # Manage DNS
          echo "192.168.56.5	controllerinfra" | sudo tee -a /etc/hosts
          echo "192.168.56.6	workerdev" | sudo tee -a /etc/hosts
          echo "192.168.56.7	workerdeploy" | sudo tee -a /etc/hosts
          echo "192.168.56.8	workermonitor" | sudo tee -a /etc/hosts
    
      SHELL
      end
    
    
    
    # Worker Deployment Machine
      config.vm.define "workerdeploy" do |workerdeploy|
        workerdeploy.vm.hostname = "worker-deploy"
        workerdeploy.vm.network "public_network", ip: "192.168.56.7", :name => 'enp0s8', :adapter => 2
        workerdeploy.vm.provider "virtualbox" do |vb|
          vb.name = "workerdeploy"
        end
        workerdeploy.vm.provision "shell", inline: <<-SHELL
          dnf install -y epel-release
          dnf update -y
          dnf install htop -y
          dnf install multitail -y
    
          # Manage DNS
          echo "192.168.56.5	controllerinfra" | sudo tee -a /etc/hosts
          echo "192.168.56.6	workerdev" | sudo tee -a /etc/hosts
          echo "192.168.56.7	workerdeploy" | sudo tee -a /etc/hosts
          echo "192.168.56.8	workermonitor" | sudo tee -a /etc/hosts
    
      SHELL
      end
    
    
    
    # Worker Monitoring Machine
      config.vm.define "workermonitor" do |workermonitor|
        workermonitor.vm.hostname = "server2"
        workermonitor.vm.network "public_network", ip: "192.168.56.8", :name => 'enp0s8', :adapter => 2
        workermonitor.vm.provider "virtualbox" do |vb|
          vb.name = "workermonitor"
        end
        workermonitor.vm.provision "shell", inline: <<-SHELL
          # Install required softwares
          dnf install -y epel-release
          dnf update -y
          dnf install htop -y
          dnf install multitail -y
    
          # Manage DNS
          echo "192.168.56.5	controllerinfra" | sudo tee -a /etc/hosts
          echo "192.168.56.6	workerdev" | sudo tee -a /etc/hosts
          echo "192.168.56.7	workerdeploy" | sudo tee -a /etc/hosts
          echo "192.168.56.8	workermonitor" | sudo tee -a /etc/hosts
    
      SHELL
      end
    
    
    
      config.ssh.username = "root"
      config.ssh.password = " "
      config.ssh.insert_key = false
      config.ssh.forward_agent = true
    
    end


`PS C:\Users\uniqs> cd 'D:\Server Snaps\Vagrant Project\rhel-92-vagrantbox'`

`PS D:\Server Snaps\Vagrant Project\rhel-92-vagrantbox> vagrant up`

`PS D:\Server Snaps\Vagrant Project\rhel-92-vagrantbox> vagrant status`

`PS D:\Server Snaps\Vagrant Project\rhel-92-vagrantbox> vagrant ssh server1`

`PS D:\Server Snaps\Vagrant Project\rhel-92-vagrantbox> vagrant ssh server2`

`PS D:\Server Snaps\Vagrant Project\rhel-92-vagrantbox> vagrant reload server1`

`PS D:\Server Snaps\Vagrant Project\rhel-92-vagrantbox> vagrant halt`

<br>
