# Analytics environment
An easy to deploy analytics environment with Jupyter and RStudio.
To use this environment you will need:
* Vagrant: Tested version 2.2.7 (https://www.vagrantup.com/)
  * vagrant plugin: vagrant-vbguest
* Virtualbox: Tested version 6.1.4 (https://www.virtualbox.org/wiki/Downloads)

## Install needed software
Install Vagrant and Virtualbox. 
After installation please install vagrant-vbguest plugin just running this command in terminal or shell:

> vagrant plugin install vagrant-vbguest

## Install analytics platform and start

Clone this repo: 

> git clone https://github.com/moyanojv/analytics.git

Enter analytics folder

> cd analytics

Start the system

> vagrant up

The first startup will take a while. The system will download and install everything for you.
And the end of the install process you will see something like:

> default: ------------------------------------------------------   
> default: IPs:    
> default:     inet 10.0.2.XXX/24 brd 10.0.2.255 scope global dynamic enp0s3    
> default:     inet 192.168.1.XXX/24 brd 192.168.1.255 scope global dynamic enp0s8    
> default: ------------------------------------------------------   

To enter Jupyter or RStudio you need to use the IP in your home range of IP's. For example:

* http://192.168.1.XXX:8888 (Jupyter)
* http://192.168.1.XXX:8787 (RStudio)

## Working directory
Inside analytics folder you will see a sub-folder called 'home' this folder will be mounted inside Jupyter and RStudio and shared between applications. All the content will be shared in real time in you computer, Jupyter and RStudio.

## Stop analytics platform
Enter analytics folder

> cd analytics

Start the system

> vagrant halt

## Destroy analytics platform
Enter analytics folder

> cd analytics

Start the system

> vagrant destroy

This command will destroy the virtual machine and dockers the content inside 'home' folder will remain.

## How it works
This is a vagrant machine (Ubuntu 18.4) that runs a couple of dockers inside (Jupyter and RStudio). dockers exposes port 8888 for Jupyter and 8787 for RStudio. The vagrant machine uses a public IP so it is possible to access the dockers using vagrant public IP.

## Previous work and adknowledge
This work is based on:
* vagrant box ubuntu/bionic64: 
  * https://app.vagrantup.com/ubuntu/boxes/bionic64
* Jupyter container: 
  * https://hub.docker.com/r/jupyter/datascience-notebook/  
  * https://jupyter-docker-stacks.readthedocs.io/en/latest/using/selecting.html#jupyter-datascience-notebook
* RStudio container:
  * https://hub.docker.com/r/rocker/rstudio/





