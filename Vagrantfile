CENTOS_BOX = "centos/7"
ELASTIC_IP = "192.168.20.10"

Vagrant.configure("2") do |config|
  # NODE 01: ELASTIC
  config.vm.define "elastic" do |elastic|
    elastic.vm.box = CENTOS_BOX
    elastic.ssh.forward_agent = true
    elastic.vm.network :private_network, ip: ELASTIC_IP
    # elastic.vm.network "public_network"
    elastic.vm.network "forwarded_port", guest: 80, host: 8080, auto_correct: true
    elastic.vm.network "forwarded_port", guest: 9200, host: 9200, auto_correct: true
    elastic.vm.network "forwarded_port", guest: 5601, host: 5601, auto_correct: true

    elastic.vm.provision "ansible" do |ansible|
      ansible.playbook = "site.yml"
      ansible.inventory_path = "hosts"
      ansible.verbose = "v"
      ansible.sudo = true
    end

  end
  # NODE 02: LOGSTASH

  # NODE 03: KIVANA

  # NODE 04: APP
  
end
