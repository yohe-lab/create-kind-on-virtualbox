# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.synced_folder './ansible', '/home/vagrant/ansible',
                          create: true, owner: 'vagrant', group: 'vagrant'
  
  # LB/workspace machine
  config.vm.define "kind-0" do |c|
    c.vm.box = "bento/rockylinux-8"
    c.vm.boot_timeout = 600
    c.vm.hostname = "kind-0"
    c.vm.network "private_network", ip: "10.240.0.30"
    c.vm.provider "virtualbox" do |vb|
      vb.cpus = "2"
      vb.memory = "4096"
      vb.customize [ "modifyvm", :id, "--uartmode1", "disconnected" ]
    end

    c.vm.provision "ansible_local" do |ansible|
      ansible.playbook = '/home/vagrant/ansible/site.yml'
      ansible.inventory_path = '/home/vagrant/ansible/inventory/client'
      ansible.limit = 'all'
    end
  end
end