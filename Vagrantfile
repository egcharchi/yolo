Vagrant.configure("2") do |config|
   config.vm.box = "geerlinguy/ubuntu2004"
   config.vm.hostname = "yolovm"
   config.vm.provider "virtualbox" do |virtualbox|
      virtualbox.memory = "2048"
   end
   config.vm.network "private_network", ip: "192.168.3.53"
   config.vm.provision "ansible" do |ansible|
     ansible.playbook = "playbook.yml"
   end
 end
 