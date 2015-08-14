# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.

Vagrant.configure(2) do |config|
  config.vm.box = "puppetlabs/debian-7.8-64-puppet"

  config.vm.network :forwarded_port, guest: 5601, host: 5601
  config.vm.network :forwarded_port, guest: 9200, host: 9200
  config.vm.network :forwarded_port, guest: 9300, host: 9300

  config.vm.synced_folder "code", "/etc/puppetlabs/code"


  config.vm.provider :virtualbox do |vb|
      vb.customize ["modifyvm", :id, "--memory", "2048"]
  end

  config.vm.provision "shell", path: 'setup.sh'

  config.vm.provision "puppet" do |puppet|
    puppet.options = '--verbose'
    puppet.environment = 'test'
    puppet.environment_path = ["vm", "/etc/puppetlabs/code/environments" ]
  end
end