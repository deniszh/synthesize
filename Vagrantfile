# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
	config.vm.define "graph001" do |graph001|
      graph001.vm.box = "mayflower/trusty64-puppet3"
	  graph001.vm.network "private_network", ip: "192.168.50.2"
      graph001.vm.network :forwarded_port, guest: 443, host: 8443
	  graph001.vm.network :forwarded_port, guest: 8125, host: 8125, protocol: 'tcp'
	  graph001.vm.network :forwarded_port, guest: 8125, host: 8125, protocol: 'udp'
	  graph001.vm.network :forwarded_port, guest: 2003, host: 22003
	  graph001.vm.network :forwarded_port, guest: 2004, host: 22004
	  graph001.vm.network :forwarded_port, guest: 3000, host: 3030
      graphite_version = ENV['GRAPHITE_RELEASE'].nil? ? 'master' : ENV['GRAPHITE_RELEASE']
	  graph001.vm.provision "shell", inline: "cd /vagrant; GRAPHITE_RELEASE=#{graphite_version} ./install"
    end

	config.vm.define "graph002" do |graph002|
      graph002.vm.box = "mayflower/trusty64-puppet3"
	  graph002.vm.network "private_network", ip: "192.168.50.3"
      graph002.vm.network :forwarded_port, guest: 443, host: 9443
      graph002.vm.network :forwarded_port, guest: 8125, host: 9125, protocol: 'tcp'
      graph002.vm.network :forwarded_port, guest: 8125, host: 9125, protocol: 'udp'
      graph002.vm.network :forwarded_port, guest: 2003, host: 32003
      graph002.vm.network :forwarded_port, guest: 2004, host: 32004
      graph002.vm.network :forwarded_port, guest: 3000, host: 4030
      graphite_version = ENV['GRAPHITE_RELEASE'].nil? ? 'master' : ENV['GRAPHITE_RELEASE']
      graph002.vm.provision "shell", inline: "cd /vagrant; GRAPHITE_RELEASE=#{graphite_version} ./install"
   end

	config.vm.define "master" do |master|
      master.vm.box = "mayflower/trusty64-puppet3"
      master.vm.network "private_network", ip: "192.168.50.4"
      master.vm.network :forwarded_port, guest: 443, host: 10443
      master.vm.network :forwarded_port, guest: 8125, host: 10125, protocol: 'tcp'
      master.vm.network :forwarded_port, guest: 8125, host: 10125, protocol: 'udp'
      master.vm.network :forwarded_port, guest: 2003, host: 42003
      master.vm.network :forwarded_port, guest: 2004, host: 42004
      master.vm.network :forwarded_port, guest: 3000, host: 5030
      graphite_version = ENV['GRAPHITE_RELEASE'].nil? ? 'master' : ENV['GRAPHITE_RELEASE']
      master.vm.provision "shell", inline: "cd /vagrant; GRAPHITE_RELEASE=#{graphite_version} ./install"
   end
end
