# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box_check_update = false
  config.vm.boot_timeout = 300
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "4096"
  end
  config.vm.define "debian11" do |deb|
    deb.vm.hostname = "dev01"
    deb.vm.box = "generic/debian11"
    deb.vm.network "private_network", ip: "192.168.56.10"
    deb.vm.synced_folder "./shared", "/shared"
    deb.vm.provision "ansible" do |ansible|
      ansible.playbook = "./ansible/playbooks/hashi-stack.yml"
      #ansible.tags = "vault-init"
    end
  end
end
