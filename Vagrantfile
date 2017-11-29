# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.define "skeleton" do |srv|
    srv.vm.box = "ubuntu/xenial64"
    srv.vm.hostname = "skeleton"
    srv.vm.network "private_network", ip: "192.168.55.110"
    srv.vm.provider "virtualbox" do |vb|
      vb.memory = "4069"
    end
    srv.vm.provision "ansible" do |ansible|
      ansible.playbook = "playbook.yml"
      ansible.skip_tags = ['packer']
      ansible.extra_vars = {
        fake_consul_data: true,
        docker_enable_fluentd: false,
        debugging_mode: true
      }
      ansible.verbose = true
    end
  end
end
