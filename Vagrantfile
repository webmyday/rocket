# -*- mode: ruby -*-
# vi: set ft=ruby :

require_relative 'vars.rb'
include MyVars

Vagrant.configure("2") do |config|

## Port Forwards
#
  config.vm.network "forwarded_port", guest: 22, host: 2200, protocol: "tcp"
  config.vm.network "forwarded_port", guest: 8010, host: 8010, protocol: "tcp"

## Hostmanager
#

  config.hostmanager.enabled = true
  config.hostmanager.manage_host = true
  config.hostmanager.manage_guest = true
  config.hostmanager.ignore_private_ip = false
  config.hostmanager.include_offline = true
  config.vm.hostname = HOSTNAME
#  config.hostmanager.aliases = %w(example-box.localdomain example-box-alias)

## VirtualBox boxes (--provider=virtualbox)
  config.vm.box = "ubuntu/xenial64"

## VMWare boxes
#  config.vm.box = "phusion/ubuntu-14.04-amd64"
#  config.vm.box = "bento/ubuntu-16.04"
#  config.vm.synced_folder "C:\\Data\\Work\\Temp", "/api"


## VMare provider host
#  config.vm.provider :vmware_workstation do |vb|
#      vb.name = "dockerhost"
#	  vb.memory = 4096
#	  vb.cpus = 2
#	  vb.gui = true
#  end

## Virtualbox provider host
   config.vm.provider "virtualbox" do |vb|
#      vb.name = "dockerhost"
	  vb.memory = 4096
	  vb.cpus = 2
#	  vb.gui = true
   end	


  config.vm.provision "shell", inline: "mkdir -p /volumes/data;chmod 777 /volumes/data; [ $BASE_FOLDER ] || echo \". /vagrant/set_env.sh\" >> ~/.profile"
#  config.vm.provision "shell", inline: "mkdir -p /volumes/jenkins_home;chmod 777 /volumes/jenkins_home; [ -f /volumes/jenkins_home/pvkey.pub ] || tar -xzf /vagrant/Docker/Jenkins/jenkins-home.tgz -C /"
#  config.vm.provision "shell", inline: "mkdir -p /volumes/fs;chmod 777 /volumes/fs"


  config.vm.provision :docker
#  config.vm.provision :docker_compose, yml: "/vagrant/docker-compose.yml", run: "always"
  config.vm.provision :docker_compose, compose_version: "1.22.0", yml: "/vagrant/docker-compose.yml", options: "--project-directory /vagrant", run: "always"
#  config.vm.provision :docker_compose, yml: "/vagrant/Docker/Mysql/docker-compose.yml", run: "always"
#  config.vm.provision :docker_compose, yml: "/vagrant/Docker/Jenkins/docker-compose.yml", run: "always"
#  config.vm.provision :docker_compose, yml: "/vagrant/Docker/PDI/docker-compose.yml", run: "always"
#  config.vm.provision :docker_compose, yml: "/vagrant/docker-compose.yml", rebuild: true, run: "always"

#  config.vm.provision :docker_compose, yml: "/vagrant/docker-compose.yml", rebuild: true,
#    options: "--x-networking", command_options: { rm: "", up: "-d --timeout 20"}, run: "always"

end