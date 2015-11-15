# -*- mode: ruby -*-
# vi: set ft=ruby :
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.synced_folder ".", "/vagrant", disabled: true
  config.vm.provider :virtualbox do |vb, override|
    vb.customize ["modifyvm", :id, "--memory", "512"]
    vb.customize ["modifyvm", :id, "--cpus", "2"]
  end
  config.vm.provider "vmware_fusion" do |vm, override|
    override.vm.box = "CorbanRaun/trusty64"
    vm.vmx["memsize"] = "512"
    vm.vmx["numvcpus"] = "2"
  end
  config.vm.define "letsencrypt" do |rundmc|
    rundmc.vm.hostname = "letsencrypt"
    rundmc.vm.provision "ansible" do |ansible|
      ansible.limit = 'all'
      ansible.playbook = "vagrant.yml"
      ansible.verbose = 'vvvv'
    end
  end
end
