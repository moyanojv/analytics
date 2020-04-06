# -*- mode: ruby -*-
# vi: set ft=ruby :

memory=4096
cpus=6

$docker_versions = <<-SCRIPT
echo "------------------------------------------------------"
echo "Docker and docker-compose versions:"
docker --version
/usr/local/bin/docker-compose --version
echo "------------------------------------------------------"
SCRIPT

$run_dockers = <<-SCRIPT
echo "------------------------------------------------------"
echo "Starting dockers:"
cd /vagrant/docker; /usr/local/bin/docker-compose up -d
echo "------------------------------------------------------"
SCRIPT

$show_ips = <<-SCRIPT
echo "------------------------------------------------------"
echo "IPs:"
ip addr show | grep dynamic
echo "------------------------------------------------------"
SCRIPT


Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"
  config.vm.network "public_network"
  config.vm.synced_folder ".", "/vagrant", disabled: false
  config.vm.provision "step1", type: "shell", path: "provision.sh"
  config.vm.provision "step2", after: "step1", type: "shell", privileged: false, inline: $docker_versions, run: "always"
  config.vm.provision "step3", after: "step2", type: "shell", privileged: true, inline: $run_dockers, run: "always"
  config.vm.provision "step4", after: "step3", type: "shell", privileged: false, inline: $show_ips, run: "always"
  config.vm.provider "virtualbox" do |vb|
     vb.memory = memory
	 vb.cpus = cpus
  end
end