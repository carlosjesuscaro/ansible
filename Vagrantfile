Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-22.04"

  config.vm.network "public_network", :bridge => "wlp0s20f3"

  config.vm.synced_folder "./data/", "/vagrant_data"

   config.vm.provider "virtualbox" do |vb|
     vb.memory = 4096
     vb.cpus = 2
     vb.name="MachineX"
   end

  config.vm.provision "shell", inline: <<-SHELL
    apt update && apt upgrade -y
    apt install curl git vim -y
  SHELL
end
