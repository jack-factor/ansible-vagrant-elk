CENTOS_BOX = "centos/7"
ELASTIC_IP = "192.168.20.10"
LOGSTASH_IP = "192.168.20.20"
KIBANA_IP = "192.168.20.30"

Vagrant.configure("2") do |config|
  # NODE 01: ELASTIC
  config.vm.define "elastic", primary: true do |elastic|
    elastic.vm.box = CENTOS_BOX
    elastic.ssh.forward_agent = true
    elastic.vm.network :private_network, ip: ELASTIC_IP
    elastic.vm.network "public_network"
    elastic.vm.network "forwarded_port", guest: 80, host: 8080, auto_correct: true
    elastic.vm.network "forwarded_port", guest: 9200, host: 9200, auto_correct: true
    elastic.vm.hostname = "elastic"

    elastic.vm.provider :virtualbox do |v|
      v.memory = 1024
      v.cpus = 2
      # v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      # v.customize ["modifyvm", :id, "--memory", "2048"]
    end 

  end

  # NODE 02: LOGSTASH
  config.vm.define "logstash" do |logstash|
    logstash.vm.box = CENTOS_BOX
    logstash.ssh.forward_agent = true
    logstash.vm.network :private_network, ip: LOGSTASH_IP
    logstash.vm.network "public_network"
    logstash.vm.network "forwarded_port", guest: 80, host: 8080, auto_correct: true
    logstash.vm.network "forwarded_port", guest: 5959, host: 5959, auto_correct: true
    logstash.vm.hostname = "logstash"
  end
  # NODE 03: KIBANA
  config.vm.define "kibana" do |kibana|
    kibana.vm.box = CENTOS_BOX
    kibana.ssh.forward_agent = true
    kibana.vm.network :private_network, ip: KIBANA_IP
    kibana.vm.network "public_network"
    kibana.vm.network "forwarded_port", guest: 80, host: 8080, auto_correct: true
    kibana.vm.network "forwarded_port", guest: 5601, host: 5601, auto_correct: true
    kibana.vm.hostname = "kibana"
  end
  # NODE 04: APP
  # Install avahi on all machines  
  config.vm.provision "shell", inline: <<-SHELL
    yum install -y avahi-daemon libnss-mdns
  SHELL

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "site.yml"
    ansible.inventory_path = "hosts"
    ansible.verbose = "v"
    ansible.sudo = true
  end
  
end
