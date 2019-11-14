CENTOS_BOX = "centos/7"
ELASTIC_IP = "192.168.20.10"

Vagrant.configure("2") do |config|
  config.vm.define "elastic" do |elastic|
    elastic.vm.box = CENTOS_BOX
    elastic.ssh.forward_agent = true
    elastic.vm.network :private_network, ip: ELASTIC_IP


    elastic.vm.provision "ansible" do |ansible|
      ansible.playbook = "site.yml"
      ansible.inventory_path = "hosts"
      ansible.verbose = "v"
      ansible.sudo = true
    end

  end

  
end
