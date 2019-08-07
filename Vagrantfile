# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box = "geerlingguy/ubuntu1604"

  config.vm.define "node1" do |box|
    box.vm.hostname = "node1"
    box.vm.network :private_network, ip: "10.10.10.10"

    box.vm.provision "shell", inline: <<-SHELL
      apt-get install -y bridge-utils jq

      cp /vagrant/k3s /usr/local/bin/k3s
      chmod +x /usr/local/bin/k3s

      mkdir -p /etc/cni/net.d
      cp /vagrant/10-my-cni-demo_node1.conf /etc/cni/net.d/10-my-cni-demo.conf

      mkdir -p /opt/cni/bin
      cp /vagrant/loopback /opt/cni/bin/loopback
      cp /vagrant/my-cni-demo /opt/cni/bin/my-cni-demo
      chmod +x /opt/cni/bin/loopback
      chmod +x /opt/cni/bin/my-cni-demo
    SHELL

  end

  config.vm.define "node2" do |box|
    box.vm.hostname = "node2"
    box.vm.network :private_network, ip: "10.10.10.11"

    box.vm.provision "shell", inline: <<-SHELL
      apt-get install -y bridge-utils jq

      cp /vagrant/k3s /usr/local/bin/k3s
      chmod +x /usr/local/bin/k3s

      mkdir -p /etc/cni/net.d
      cp /vagrant/10-my-cni-demo_node2.conf /etc/cni/net.d/10-my-cni-demo.conf

      mkdir -p /opt/cni/bin
      cp /vagrant/loopback /opt/cni/bin/loopback
      cp /vagrant/my-cni-demo /opt/cni/bin/my-cni-demo
      chmod +x /opt/cni/bin/loopback
      chmod +x /opt/cni/bin/my-cni-demo
    SHELL

  end

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "1024"
  end

end
