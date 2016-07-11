# -*- mode: ruby -*-
# vi: set ft=ruby :

require "yaml"
hosts = YAML.load(File.open(File.join(File.dirname(__FILE__),"docker_hosts.yaml"), File::RDONLY).read)['hosts']

Vagrant.configure("2") do |config|
  config.vm.box = "lazzurs/boot2docker"
  hosts.each do |host|
    config.vm.define host['name'] do |c|
      c.vm.network :private_network, ip: host['ip'], netmask: '255.255.255.0'
      c.vm.hostname = host['name']
      c.vm.provision "shell", inline: host['provision']
    end
  end
end
