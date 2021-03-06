Vagrant.configure("2") do |config|
  # Basic stuff, used box and hostname
  config.vm.hostname = "appenlight.dev"
  config.vm.box = "bento/ubuntu-18.04"
  config.vm.box_version = "201912.14.0"

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
  config.vm.synced_folder ".", "/home/vagrant/.for_provisioning"

  # Run provisioning scripts

  config.vm.provision "shell",
      inline: "sudo apt-get install python3-dev python3-pip python3-venv python3-psycopg2 -y -qq && "\
        "sudo python3 -m venv /root/ansible_venv && "\
        "sudo /root/ansible_venv/bin/pip install ansible==2.9.4 psycopg2-binary && "\
        "sudo /root/ansible_venv/bin/ansible-playbook -i localhost, -c local /home/vagrant/.for_provisioning/ansible/provision_appenlight_vm.yaml \\"\
        "-e@/home/vagrant/.for_provisioning/ansible/appenlight_vm_extra_vars.yaml"

  config.vm.provider "vmware_fusion" do |v|
      v.gui = false
      v.vmx["memsize"] = "4096"
      v.vmx["numvcpus"] = "2"
  end

  config.vm.provider "virtualbox" do |vb|
     vb.gui = false
     vb.name = "appenlight.dev"
     vb.memory = 4096
     vb.cpus = 2
   end
end
