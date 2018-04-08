# -*- mode: ruby -*-
# vi: set ft=ruby :

$bootstrap = <<SCRIPT

# compatability
sudo dpkg --add-architecture i386
sudo apt-get update
sudo apt-get upgrade

# git
sudo apt-get -fuy -o Dpkg::Options::='--force-confold' install git

# qemu
sudo apt-get install qemu

# gdb
sudo apt-get install gdb

# radare2
git clone https://github.com/radare/radare2.git ~/radare2
sudo ~/radare2/sys/install.sh

# pwntools
sudo apt-get -y install python2.7 python-pip python-dev git libssl-dev libffi-dev build-essential
sudo pip install --upgrade pip
sudo pip install --upgrade pwntools

# gdb-peda
git clone https://github.com/longld/peda.git ~/peda
echo "source ~/peda/peda.py" >> ~/.gdbinit

# x86_32 support
sudo apt-get install libc6:i386 libncurses5:i386 libstdc++6:i386 multiarch-support

SCRIPT

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.hostname = "ctf-vm"
  config.vm.provision "shell", privileged: false, inline: $bootstrap
  config.vbguest.installer_arguments = []
end
