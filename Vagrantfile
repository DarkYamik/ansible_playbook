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
        podmanubuntu1804.vm.box = "ubuntu/bionic64"
        podmanubuntu1804.vm.box_check_update = true
        podmanubuntu1804.vm.hostname = "podmanubuntu1804"
        podmanubuntu1804.vm.network "public_network", auto_config: true
        podmanubuntu1804.vm.provider "virtualbox" do |v|
            v.name = "podmanubuntu1804"
            v.memory = "512"
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
end
