VM building

1. download and unpack packer from https://www.packer.io/downloads.html into ./packer
2. You also need to have ansible 2.1+ installed on your machine (active virtualenv will do)
3. run the command

./packer build vm_type.json

When packer finishes we will get a working application
