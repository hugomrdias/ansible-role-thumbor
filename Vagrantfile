# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.hostname = "thumbor.local"
  config.vm.network "forwarded_port", guest: 80, host: 9000
  config.vm.network "private_network", ip: "192.168.11.20"

  config.vm.provision 'ansible' do |ansible|
    ansible.playbook = 'tests/test.yml'
    ansible.inventory_path = 'tests/inventory'
    ansible.limit = 'vagrant'
    ansible.sudo = true
    ansible.verbose = 'vvv'
    # ansible.extra_vars = {
    #   nginx_install_method: nginx_install_method
    # }
  end
end