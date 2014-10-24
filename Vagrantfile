# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "just-linux"
  config.vm.box_url = "http://files.vagrantup.com/precise64.box"

  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--cpus", "2", "--memory", "1536"]
  end

  config.vm.define :master do |master|
    master.vm.network "private_network", ip: "192.168.7.10"
    master.vm.hostname = "master.local"

    config.vm.provision :puppet do |puppet|
      puppet.manifest_file = "master.pp"
      puppet.module_path = "modules"
      puppet.manifests_path = "manifests"
    end
  end
end
