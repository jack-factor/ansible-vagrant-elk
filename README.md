VAGRANT ELK
=================================================

Description:
-----------

Virtualbox and vagrant used to build virtual machines as servers.  

Prerequisites / Requirements
----------------------------
install these requirements

1. Download and Install [VitualBox](https://www.virtualbox.org/wiki/Downloads)
2. Download and Install [Vagrant](https://www.vagrantup.com/downloads.html)
3. Install [guest additions to Vagrant](https://github.com/dotless-de/vagrant-vbguest)  
 `vagrant plugin install vagrant-vbguest`
4. Install [vagrant hostmanager](https://github.com/devopsgroup-io/vagrant-hostmanager)  
 `vagrant plugin install vagrant-hostmanager`
5. Install [Ansible](http://docs.ansible.com/ansible/intro_installation.html).  
  `sudo pip install ansible`
5. Install [Git](https://git-scm.com/).  

Getting Started
---------------
1. clone this repository:
  `git clone git@github.com:jack-factor/ansible-vagrant-elk.git`
2. Start Vagrant VM:
  `vagrant up`
4. Open your browser:
  `http://kibana:5601`
  `http://elastic:9600`