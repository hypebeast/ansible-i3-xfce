# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "ubuntu/xenial64"
  # config.ssh.insert_key = false

  config.vm.provider :virtualbox do |v|
    v.name = "i3-xfce"
    v.memory = 512
    v.cpus = 1
    # v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    v.customize ["modifyvm", :id, "--ioapic", "on"]
  end

  config.vm.hostname = "i3xfce"
  config.vm.network :private_network, ip: "192.168.33.27"

  # Ansible provisioner.
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "vagrant.yml"
    #ansible.inventory_path = "provisioning/inventory"
    ansible.sudo = true
  end

end
