# Vagrant

Just run `vagrant up`.

The application will be listening on `127.0.0.1:8001` and `appenlight_dev:8001`.

Login and pass for sudo user `vagrant:vagrant`.

The image has `appenlight` and `channelstream` users for application itself.


# VM building

1. download and unpack packer from https://www.packer.io/downloads.html

       wget https://releases.hashicorp.com/packer/1.4.0/packer_1.4.0_linux_amd64.zip
       unzip packer_1.4.0_linux_amd64.zip

2. You also need to have ansible 2.5+ installed on your machine 
   (active virtualenv will do, your distribution should also provide `ansible` package)

3. build images

HTTP server will be resolving the app on 127.0.0.1 or `appenlight_dev` domains.

Login and pass for sudo user `ubuntu:ubuntu`.

# Examples:

VirtualBox: 

    # build base OS image
    ./packer build ubuntu_18_04_virtualbox_ova.json
    # build AppEnlight image out of pure ubuntu OVA
    ./packer build appenlight_ce_virtualbox_ova.json

When packer finishes we will get a working application.
