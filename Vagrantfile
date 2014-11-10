# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = '2'

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = 'hashicorp/precise64'

  config.vm.define(vm_name = 'squid') do |config|
    config.vm.hostname = vm_name
    config.vm.base_mac = '080000000101'
    config.vm.network :private_network, ip: '192.168.56.101', mac: '080000000102'
    config.vm.provision :ansible do |ansible|
      ansible.playbook = 'main.yml'
      ansible.sudo     = true
    end
  end
end
