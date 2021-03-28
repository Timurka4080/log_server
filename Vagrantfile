# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "centos/7"

  config.vm.provision "ansible" do |ansible|
    ansible.verbose = "v"
    ansible.playbook = "provisioning/playbook.yml"
    ansible.sudo = "true"
  end


  config.vm.provider "virtualbox" do |v|
	  v.memory = 512
  end

  config.vm.define "server-log" do |server_log|
    server_log.vm.network "private_network", ip: "192.168.50.10", virtualbox__intnet: "dns"
    server_log.vm.hostname = "server-log"
  end

  config.vm.define "client" do |client|
    client.vm.network "private_network", ip: "192.168.50.15", virtualbox__intnet: "dns"
    client.vm.hostname = "client"
  end
end
