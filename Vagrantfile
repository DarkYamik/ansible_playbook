# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
    # Disbled synced folder
    config.vm.synced_folder ".", "/vagrant", disabled: true

    # Enable hostnamager plugins to use hostname in Ansible inventory
    config.hostmanager.enabled = true
    config.hostmanager.manage_host = true
    config.hostmanager.manage_guest = true
    config.hostmanager.ignore_private_ip = true
    config.hostmanager.include_offline = true

    # Ubuntu 18.04 (Bionic)
    config.vm.define "ubuntu1804", autostart: false do |ubuntu1804|
        ubuntu1804.vm.box = "ubuntu/bionic64"
        ubuntu1804.vm.box_check_update = true
        ubuntu1804.vm.hostname = "ubuntu1804"
        ubuntu1804.vm.network "public_network", auto_config: true
        ubuntu1804.vm.provider "virtualbox" do |v|
            v.name = "ubuntu1804"
            v.memory = "512"
            v.cpus = 1
        end
        ubuntu1804.hostmanager.ip_resolver = proc do |vm, resolving_vm|
            if hostname = (vm.ssh_info && vm.ssh_info[:host])
                `vagrant ssh ubuntu1804 -c "hostname -I"`.split()[1]
            end
        end

        # Necessary for ansible
        ubuntu1804.vm.provision "shell", inline: "sudo apt-get -y install python python-apt"
    end

        # Ubuntu 18.04 Podman(Bionic)
    config.vm.define "podmanubuntu1804", autostart: false do |podmanubuntu1804|
        podmanubuntu1804.vm.box = "generic/ubuntu1804"
        
        podmanubuntu1804.vm.box_check_update = true
        podmanubuntu1804.vm.hostname = "podmanubuntu1804"
        podmanubuntu1804.vm.disk :disk,  name: "main", size: "20GB"
        podmanubuntu1804.vm.network "public_network", auto_config: true
        podmanubuntu1804.vm.provider "virtualbox" do |v|
            v.name = "podmanubuntu1804"
            v.memory = "2048"
            v.cpus = 1
           
        end
        podmanubuntu1804.hostmanager.ip_resolver = proc do |vm, resolving_vm|
            if hostname = (vm.ssh_info && vm.ssh_info[:host])
                `vagrant ssh podmanubuntu1804 -c "hostname -I"`.split()[1]
            end
        end

        # Necessary for ansible
        podmanubuntu1804.vm.provision "shell", inline: "sudo apt-get -y install python python-apt"

    end

            # Ubuntu 18.04 Mysqlmaster
    config.vm.define "mysqlmaster", autostart: false do |mysqlmaster|
        mysqlmaster.vm.box = "generic/ubuntu1804"
        mysqlmaster.vm.box_check_update = true
        mysqlmaster.vm.hostname = "mysqlmaster"
        mysqlmaster.vm.network "public_network", auto_config: true
        mysqlmaster.vm.provider "virtualbox" do |v|
            v.name = "mysqlmaster"
            v.memory = "512"
            v.cpus = 1
            
        end
        mysqlmaster.hostmanager.ip_resolver = proc do |vm, resolving_vm|
            if hostname = (vm.ssh_info && vm.ssh_info[:host])
                `vagrant ssh mysqlmaster -c "hostname -I"`.split()[1]
            end
        end

        # Necessary for ansible
        mysqlmaster.vm.provision "shell", inline: "sudo apt-get -y install python python-apt"
    end

                # Ubuntu 18.04 Mysqlslave
    config.vm.define "mysqlslave", autostart: false do |mysqlslave|
        mysqlslave.vm.box = "generic/ubuntu1804"
        mysqlslave.vm.box_check_update = true
        mysqlslave.vm.hostname = "mysqlslave"
        mysqlslave.vm.network "public_network", auto_config: true
        mysqlslave.vm.provider "virtualbox" do |v|
            v.name = "mysqlslave"
            v.memory = "512"
            v.cpus = 1
        end
        mysqlslave.hostmanager.ip_resolver = proc do |vm, resolving_vm|
            if hostname = (vm.ssh_info && vm.ssh_info[:host])
                `vagrant ssh mysqlslave -c "hostname -I"`.split()[1]
            end
        end

        # Necessary for ansible
        mysqlslave.vm.provision "shell", inline: "sudo apt-get -y install python python-apt"
    end
end
