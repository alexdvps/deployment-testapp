# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = '2'

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.define 'ansible-testapp' do |machine|
    machine.vm.box = 'ubuntu/xenial64'

    machine.vm.hostname = 'ansible-testapp'
    machine.vm.synced_folder '.', '/vagrant', disabled: true

    machine.vm.provision "ansible" do |ansible|
      ansible.limit = "all"
      ansible.verbose = "v"
      ansible.playbook = "ansible/playbook.yml"
    end
  end
end
