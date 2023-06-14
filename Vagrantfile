# -*- mode: ruby -*-
# vi: set ft=ruby :
#
MEMORY = 1024
CPU = 1
IP_LB = "192.168.56.10" 
IP_WEB1 = "192.168.56.11"
IP_WEB2 = "192.168.56.12"

Vagrant.configure("2") do |config|

  config.vm.define "lb" do |lb|
   lb.vm.box = "ubuntu/xenial64"
   lb.vm.network "private_network", ip: IP_LB
   lb.vm.provision "shell" do |s|
     s.path = "https://raw.githubusercontent.com/a-farsi/nginx-load-balancer-in-shell/main/lb.sh"
   end
  end
  config.vm.provider "virtualbox" do |v|
     v.memory = MEMORY
     v.cpus = CPU
  end


  config.vm.define "web1" do |web1|
    web1.vm.box = "ubuntu/xenial64"
    web1.vm.hostname = "web1"
    web1.vm.network "private_network", ip: IP_WEB1
    web1.vm.provision "shell" do |s|
      s.path = "https://raw.githubusercontent.com/a-farsi/nginx-load-balancer-in-shell/main/web.sh"
      s.args   = "1"
    end
  end
  config.vm.provider "virtualbox" do |v|
     v.memory = MEMORY
     v.cpus = CPU
  end
  config.vm.define "web2" do |web2|
   web2.vm.box = "ubuntu/xenial64"
   web2.vm.hostname = "web2"
   web2.vm.network "private_network", ip: IP_WEB2
   web2.vm.provision "shell" do |s|
     s.path = "https://raw.githubusercontent.com/a-farsi/nginx-load-balancer-in-shell/main/web.sh"
     s.args   = "2"
   end
  end
  config.vm.provider "virtualbox" do |v|
     v.memory = MEMORY
     v.cpus = CPU
  end
end

