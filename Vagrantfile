# -*- mode: ruby -*-
# vi: set ft=ruby :


BOX_IMAGE = "bento/ubuntu-16.04"
NODE_COUNT = 1 #only 1 instance of db server

Vagrant.configure("2") do |config|
	#config.vm.define "master" do |subconfig|
	#	subconfig.vm.box = BOX_IMAGE
	#end

	(1..NODE_COUNT).each do |i|
		config.vm.define "db#{i}" do |subconfig|
			subconfig.vm.box = BOX_IMAGE
			subconfig.vm.network :private_network, ip: "10.0.0.#{i + 10}"
		end
	end

	# Install avahi on all machines     
	config.vm.provision "shell", inline: <<-SHELL     
		apt-get install -y avahi-daemon libnss-mdns   
	SHELL
end