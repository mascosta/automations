#############################################################################################
#                                                                                           #
# A vagrantfile based on https://github.com/cheretbe/packer-routeros/blob/master/README.md  #
# This script can bring up some network interfaces for management.                          #
# Author: Marcus Costa                                                                      #
# Email: marcus.asc@gmail.com                                                               #
# Execution Sample: "/path/to/script/directory/vagrant up"                                  #
#                                                                                           #
#############################################################################################

Vagrant.configure("2") do |config|
# Setting up the quantity of VM's will be configured, in this case, 1 to 4.
    (1..4).each do |i| 
        # Using the number of VM "i" to compose it VirtualBox name.
        config.vm.define "mk_#{i}" do |mk|
            mk.vm.box = "cheretbe/routeros"
            # Using the number of VM "i" to compose it hostname
            mk.vm.hostname = "mk#{i}"
            mk.vm.provision "routeros_command", name: "Teste", command: "/system resource print"
            mk.vm.network "public_network", bridge: "enp1s0", auto_config: false
            mk.vm.network "private_network", virtualbox__intnet: "lan#{i}", auto_config: false
            mk.vm.provider "virtualbox" do |v| 
                # Setting up custom settings
                v.memory    = 64
                v.name      = "mk#{i}"
            end
        end
    end 
end
