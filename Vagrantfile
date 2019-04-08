Vagrant.configure("2") do |config|
  # Basic stuff, used box and hostname
  config.vm.hostname = "appenlight.dev"
  config.vm.box = "bento/ubuntu-18.04"

  # Ports configuration
  config.vm.network "forwarded_port", guest: 22, host: 2222  # ssh, it's set by default to 2222
  config.vm.network "forwarded_port", guest: 80, host: 8001  # nginx
  config.vm.network "forwarded_port", guest: 5432, host: 5433  # postgres
  config.vm.network "forwarded_port", guest: 6379, host: 6380  # redis
  config.vm.network "forwarded_port", guest: 5672, host: 5673  # rabbitmq
  config.vm.network "forwarded_port", guest: 15672, host: 15673  # rabbitmq webui
  config.vm.network "forwarded_port", guest: 9200, host: 9201  # elasticsearch
  config.vm.network "forwarded_port", guest: 8088, host: 8088  # channelstream
  config.vm.network "forwarded_port", guest: 6543, host: 6544  # points2shop

  # config.vm.synced_folder "appenlight", "/home/vagrant/appenlight"

  # Run provisioning scripts

  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "ansible/provision_appenlight_vm.yaml"
    ansible.install_mode = "pip"
    ansible.version = "2.7.1"
    ansible.extra_vars = {
        hosts: "all",
        appenlight_secure_cookies: false
    }
  end

  config.vm.provider "vmware_fusion" do |v|
      v.gui = false
      v.vmx["memsize"] = "4096"
      v.vmx["numvcpus"] = "2"
  end

  config.vm.provider "virtualbox" do |vb|
     vb.gui = false

     vb.memory = 4096
     vb.cpus = 2
     # vb.customize ["modifyvm", :id, "--cpuexecutioncap", "60"]
     # vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
     # vb.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
   end
end
