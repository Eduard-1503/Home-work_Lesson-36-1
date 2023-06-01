# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.define "ipa.otus.lan" do |srv|
    srv.vm.box = 'centos/stream8'
    srv.vm.host_name = 'ipa.otus.lan'
    # Add networks
    # srv.vm.network 'forwarded_port', guest: 80, host: 8080, protocol: 'tcp'
    # srv.vm.network :private_network, ip: '192.168.255.1', adapter: 2, netmask: "255.255.255.252", virtualbox__intnet: 'inetrouter1-net'
    srv.vm.network :private_network, ip: '192.168.56.10', adapter: 8
    # Change memory size
    srv.vm.provider :virtualbox do |vb|
      vb.memory = "2048"
    end
  end
  config.vm.provision "ansible" do |ansible|
    ansible.verbose = "vv"
    ansible.playbook = "provisioning/ipa.yaml"
    ansible.become = "true"
  end
end

Vagrant.configure("2") do |config|
  config.vm.define "client1.otus.lan" do |cl1|
    cl1.vm.box = 'centos/stream8'
    cl1.vm.host_name = 'client1.otus.lan'
    # Add networks
    # ir2.vm.network 'forwarded_port', guest: 8080, host: 8080, protocol: 'tcp'
    cl1.vm.network 'private_network', ip: '192.168.56.11', adapter: 8
    # Change memory size
    cl1.vm.provider :virtualbox do |vb|
      vb.memory = "1024"
    end
  end
end

Vagrant.configure("2") do |config|
  config.vm.define "client2.otus.lan" do |cl2|
    cl2.vm.box = 'centos/stream8'
    cl2.vm.host_name = 'client2.otus.lan'
   # Add network
    # rt_c.vm.network :private_network, ip: '192.168.255.2', adapter: 2, netmask: "255.255.255.252", virtualbox__intnet: 'inetrouter1-net'
    # rt_c.vm.network :private_network, ip: '192.168.0.1', adapter: 3, netmask: "255.255.255.240", virtualbox__intnet: 'dir-net'
    cl2.vm.network :private_network, ip: '192.168.56.12', adapter: 8
    # Change memory size
    cl2.vm.provider :virtualbox do |vb|
      vb.memory = "1024"
    end
  end
end

