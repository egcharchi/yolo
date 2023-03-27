Vagrant.configure("2") do |config|
   config.vm.box = "geerlinguy/ubuntu2004"
   config.vm.provision "ansible" do |ansible|
     ansible.playbook = "playbook.yml"
   end
 end
 