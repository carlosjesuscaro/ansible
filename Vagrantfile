# Global variable configuration
NUM_VMS = 3
VM_BOX = "bento/ubuntu-22.04"
VM_CPU = 2
VM_MEM = 2048

# Configuration
Vagrant.configure("2") do |config|
    (1..NUM_VMS).each do |i|
        config.vm.define "node-#{i}" do |node|
            node.vm.box = VM_BOX
            node.vm.network "private_network", ip: "192.168.56.#{10 + i}"
            node.vm.hostname = "machinex-#{i}"
            node.vm.provider "virtualbox" do |vb|
                vb.cpus = VM_CPU
                vb.memory = VM_MEM
                vb.name = "VM-#{i}"
            end

            # Basic update and package installation
            node.vm.provision "shell", inline: <<-SHELL
                apt update && apt upgrade -y
                apt install curl nala git vim -y
            SHELL
        end
    end
end
