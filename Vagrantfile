# -*- mode: ruby -*-
# vi: set ft=ruby  :

machines = {
  "ubuntu" => {"memory" => "2048", "cpu" => "2", "ip" => "10", "image" => "ubuntu/jammy64"}
}

Vagrant.configure("2") do |config|
  machines.each do |name, conf|
    config.ssh.extra_args = ["-t", "cd /vagrant; bash --login"]
    config.vm.define "#{name}" do |machine|
      machine.vm.box = "#{conf["image"]}"
      machine.vm.hostname = "#{name}.curso.linuxtips"
      machine.vm.network "private_network", ip: "10.10.10.#{conf["ip"]}"
      machine.vm.provider "virtualbox" do |vb|
        vb.name = "#{name}"
        vb.memory = conf["memory"]
        vb.cpus = conf["cpu"]
        vb.customize ["modifyvm", :id, "--groups", "/curso-Lab"]
      end
    end
  end
end