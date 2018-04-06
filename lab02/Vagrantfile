# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
    config.vm.define "nxos1" do |node|
        node.vm.box =  "nxos/7.0.3.I7.3"

        # The following block of configuration customizes the VM settings in virtualbox
        # and is needed if you are using the box from Cisco.com for
        # NX-OS 7.0(3)I7(3) or later and didn't run the Python script against it
        # These settings reduce the memory per switch from 8G -> 4G and
        # Disconnect the virtual serial ports to prevent overlap.

        config.vm.provider "virtualbox" do |vb|
          vb.memory = "4096"
          vb.customize ['modifyvm', :id, '--uart1', '0x3F8', 4, '--uartmode1', 'disconnected']
          vb.customize ['modifyvm', :id, '--uart2', '0x2F8', 3, '--uartmode2', 'disconnected']
        end

        # eth1/1 connected to link2,
        node.vm.network :private_network, virtualbox__intnet: "link2", auto_config: false

        # Explicity set SSH Port to avoid conflict and for provisioning
        config.vm.network :forwarded_port, guest: 22, host: 3122, id: 'ssh', auto_correct: true

        # Forward API Ports
        config.vm.network :forwarded_port, guest: 80, host: 3180, id: 'http', auto_correct: true
        config.vm.network :forwarded_port, guest: 443, host: 3143, id: 'https', auto_correct: true
        config.vm.network :forwarded_port, guest: 830, host: 3130, id: 'netconf', auto_correct: true
    end

    config.vm.define "nxos2" do |node|
        node.vm.box =  "nxos/7.0.3.I7.3"

        # The following block of configuration customizes the VM settings in virtualbox
        # and is needed if you are using the box from Cisco.com for
        # NX-OS 7.0(3)I7(3) or later and didn't run the Python script against it
        # These settings reduce the memory per switch from 8G -> 4G and
        # Disconnect the virtual serial ports to prevent overlap.

        config.vm.provider "virtualbox" do |vb|
          vb.memory = "4096"
          vb.customize ['modifyvm', :id, '--uart1', '0x3F8', 4, '--uartmode1', 'disconnected']
          vb.customize ['modifyvm', :id, '--uart2', '0x2F8', 3, '--uartmode2', 'disconnected']
        end

        # eth1/1 connected to link2,
        node.vm.network :private_network, virtualbox__intnet: "link2", auto_config: false

        # Explicity set SSH Port to avoid conflict and for provisioning
        config.vm.network :forwarded_port, guest: 22, host: 3222, id: 'ssh', auto_correct: true

        # Forward API Ports
        config.vm.network :forwarded_port, guest: 80, host: 3280, id: 'http', auto_correct: true
        config.vm.network :forwarded_port, guest: 443, host: 3243, id: 'https', auto_correct: true
        config.vm.network :forwarded_port, guest: 830, host: 3230, id: 'netconf', auto_correct: true
    end

end
