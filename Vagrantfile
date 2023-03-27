Vagrant.configure("2") do |config|
   config.vm.box = "geerlingguy/ubuntu2004"
   config.vm.hostname = "yolovm"
   config.vm.provider "virtualbox" do |virtualbox|
      virtualbox.memory = "2048"
   end
   config.vm.network "private_network", ip: "192.168.56.53"
   config.vm.network "forwarded_port", guest: 3000, host: 3000
   config.vm.provision "ansible" do |ansible|
     ansible.playbook = "playbook.yml"
   end
 end
 