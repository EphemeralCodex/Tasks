# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box = "trueability/sles-15-sp1"

   config.vm.box_check_update = false

   config.vm.network "forwarded_port", guest: 80, host: 8080

   config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"

   config.vm.network "private_network", ip: "192.168.33.10"

   config.vm.network "public_network"

   #config.vm.synced_folder "../data", "/vagrant_data"

   config.vm.provider "virtualbox" do |vb|
    #Display the VirtualBox GUI when booting the machine
     vb.gui = true

    #Customize the amount of memory on the VM:
     vb.memory = "1024"
   end


   config.vm.provision "shell", inline: <<-SHELL
   #!bin/bash
   sudo zypper --non-interactive --quiet ar obs://GNOME:STABLE:3.0/openSuse_11.4 GNOME_STABLE_3.0
   sudo zypper --non-interactive --quiet mr -p 98 -r GNOME_STABLE_3.0
   sudo zypper --non-interactive --quiet dup
   sudo zypper --non-interactive --quiet in gnome-shell metatheme-adwaita-common
   sudo zypper --non-interactive --quiet in Mesa-noveau3d
   sudo startx

   SHELL
 end
