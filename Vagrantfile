# -*- mode: ruby -*-
# vi: set ft=ruby :

NUM_WORKER_NODES=2
IP_NW="10.0.0."
IP_START=10

Vagrant.configure("2") do |config|
  config.vm.box_check_update = false

  config.vm.define "master" do |master|
    master.vm.box = "sergiosg9823/k8s-master"
    master.vm.box_version = "1.23"
    master.vm.hostname = "master-node"
    master.vm.network "private_network", ip: IP_NW + "#{IP_START}"
    master.vm.provider "virtualbox" do |vb|
        vb.memory = 4096
        vb.cpus = 2
    end
  end

  (1..NUM_WORKER_NODES).each do |i|

  config.vm.define "node0#{i}" do |node|
    node.vm.box = "sergiosg9823/k8s-node0#{i}"
    node.vm.box_version = "1.23"
    node.vm.hostname = "worker-node0#{i}"
    node.vm.network "private_network", ip: IP_NW + "#{IP_START + i}"
    node.vm.provider "virtualbox" do |vb|
        vb.memory = 4096
        vb.cpus = 2
    end
  end

  end
end
