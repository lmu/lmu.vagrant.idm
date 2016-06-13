# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

# Special Settings for this Vagrant Environment
USE_PUBLIC_NETWORK = false
#USE_PUBLIC_NETWORK = true
PRIVATE_NETWORK_BASE = "192.168.1"
#PRIVATE_NETWORK_BASE = PRIVATE_NETWORK_BASE + ""
PUBLIC_NETWORK_BASE = "137.193.211"
#PUBLIC_NETWORK_BASE = "192.168.2"
AUTOSTART_SECONDARY = false
#AUTOSTART_SECONDARY = true
AUTOSTART_INFRASTRUKTURE = false
#AUTOSTART_INFRASTRUKTURE = true

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "centos/7"

  config.ssh.forward_agent = true

  config.vm.define "idmtest1.zuv.uni-muenchen.de" do |node|
    node.vm.box = "centos/7"
    node.vm.provider "virtualbox" do |vb|
      vb.name = "IDM-Test1"
      vb.memory = 4096
      vb.cpus = 4
      vb.customize ["modifyvm", :id,
                    "--cpuexecutioncap", "50",
                    "--groups", "/Vagrant/LMU/IDM"
                   ]
    end

    node.vm.network "forwarded_port", guest: 80, host: 80
    node.vm.network "forwarded_port", guest: 443, host: 443
    node.vm.network "forwarded_port", guest: 8080, host: 8080
    node.vm.network "forwarded_port", guest: 8443, host: 8443

  end

  config.vm.provision "shell" do |shell|
    shell.inline = "apt-get install python aptitude"
  end

end
