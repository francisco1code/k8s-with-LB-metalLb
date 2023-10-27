# -*- mode: ruby -*-
# vi: set ft=ruby :

$script = <<-SCRIPT
echo I am provisioning...
sudo apt update
sudo apt install htop curl vim telnet traceroute -y
SCRIPT

Vagrant.configure("2") do |config|
  config.vm.provider "libvirt"
  config.vm.provider :libvirt do |libvirt|
    libvirt.cpus = 4
    #3GB
    libvirt.memory = 4096
  end
  config.vm.provision "shell", inline: $script
  config.vm.box = "debian/bookworm64"
  config.vm.hostname = "rancher.local"
  config.vm.synced_folder ".", "/vagrant", type: "rsync", rsync__exclude: ".git/"
end
