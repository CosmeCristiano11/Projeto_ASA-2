# -*- mode: ruby -*-
# vim: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "debian/bookworm64"
  config.vm.hostname = "caua.cosme"
  config.ssh.insert_key = false

  config.vm.network "private_network", ip: "192.168.56.136"

  config.vm.synced_folder ".", "/vagrant"

  config.vm.provider "virtualbox" do |vb|
    vb.memory = 1024
    vb.cpus   = 1
    vb.gui    = false
  end

  if Vagrant.has_plugin?("vagrant-vbguest")
    config.vbguest.auto_update = false
  end

  config.vm.provision "shell", inline: <<-SHELL
    set -e
    apt-get update -y
    apt-get install -y --no-install-recommends ansible python3
  SHELL

  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook          = "playbook_ansible.yml"
    ansible.provisioning_path = "/vagrant"
    ansible.limit             = "all"
  end
end

