# -*- mode: ruby -*-
# vi: set ft=ruby :

require 'socket'
hostname = Socket.gethostname
prefix = 'swarmnode-'
guestname = prefix + hostname

Vagrant.configure("2") do |config|
  config.vm.box_url = "https://cloud-images.ubuntu.com/xenial/current/xenial-server-cloudimg-amd64-vagrant.box"
  config.vm.box = "xenial64"
  config.vm.hostname = "#{guestname}"
  config.vm.define "#{guestname}" do |guestname|
  end
  config.vm.provider :virtualbox do |vb|
        vb.name = "#{guestname}"
  end
  config.vm.network :forwarded_port, guest: 2377, host: 2377
  config.vm.network :forwarded_port, guest: 7946, host: 7946
  config.vm.network :forwarded_port, guest: 4789, host: 4789

   config.vm.provision "shell", inline: <<-SHELL
     curl -fsSL https://test.docker.com | sh
     sudo usermod -aG docker ubuntu
   SHELL
end

