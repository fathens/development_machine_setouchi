# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/focal64"
  config.vm.define "setouchi" do |node|
    node.vm.hostname = "setouchi"
    node.vm.network :private_network, ip: "192.168.56.11"
  end
  if Vagrant.has_plugin?("vagrant-disksize")
    config.disksize.size = "500GB"
  end
  config.vm.provider "virtualbox" do |vb|
    vb.cpus = 4
    vb.memory = "16384"
    vb.customize ["modifyvm", :id, "--ioapic", "on"]
  end
  config.vm.provision "ansible" do |ansible|
    ansible.verbose = "false"
    ansible.playbook = "site.yml"
    ansible.galaxy_role_file = "requirements.yml"
    ansible.galaxy_roles_path = "~/.ansible/roles"
  end
end
