# -*- mode: ruby -*-
# vi: set ft=ruby :

$script = <<-SCRIPT
echo I am provisioning...
sudo apt update
sudo apt install htop curl vim telnet traceroute -y
SCRIPT

Vagrant.configure("2") do |config|
  config.vm.provider "virtualbox"
  config.vm.provider :virtualbox do |v|
    v.gui = false
    v.cpus = 4
    v.memory = 4096
  end

  config.vm.provision "shell", inline: $script
  config.vm.provision "shell", inline: "echo 'root:123456' | chpasswd"
  config.vm.box = "debian/bookworm64"
  config.vm.hostname = "rancher.local"
  config.vm.synced_folder ".", "/vagrant", type: "rsync", rsync__exclude: ".git/"
  config.vm.network "forwarded_port", guest: 6443, host: 6443
  config.vm.network "private_network", ip: "192.168.56.44"
end