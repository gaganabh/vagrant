#-*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.configure("2") do |config|

  config.ssh.insert_key = false

  config.vm.define "master" do |vagrant1|
    vagrant1.vm.box = "centos/7"
    vagrant1.vm.hostname = "master"
    config.vm.synced_folder "/home/gagan/", "/fota", disabled: false
    vagrant1.vm.network "forwarded_port", guest: 3000, host: 3000
    vagrant1.vm.network "private_network", ip: "10.0.0.10"
  end

  config.vm.define "jenkins" do |vagrant2|
    vagrant2.vm.box = "ubuntu/trusty64"
    vagrant2.vm.hostname = "jenkins"
    config.vm.synced_folder "/home/gagan/", "/fota", disabled: false
    vagrant2.vm.network "forwarded_port", guest: 8080, host: 8080
    vagrant2.vm.network "private_network", ip: "10.0.0.11"
    vagrant2.vm.provider :virtualbox do |vb|
     vb.customize ["modifyvm", :id, "--memory", 4096]
     vb.customize ["modifyvm", :id, "--cpus", 4]
end
  end

  config.vm.define "artifactory" do |vagrant3|
    vagrant3.vm.box = "ubuntu/trusty64"
    vagrant3.vm.hostname = "artifactory"
    config.vm.synced_folder "/home/gagan/", "/fota", disabled: false
    vagrant3.vm.network "forwarded_port", guest: 8081,host: 8081
    vagrant3.vm.network "private_network", ip: "10.0.0.12"
    vagrant3.vm.provider :virtualbox do |vb|
     vb.customize ["modifyvm", :id, "--memory", 4096]
     vb.customize ["modifyvm", :id, "--cpus", 4]
end
end
   config.vm.define "node3" do |vagrant4|
    vagrant4.vm.box = "ubuntu/trusty64"
    vagrant4.vm.hostname = "node3"
    vagrant4.vm.network "private_network", ip: "10.0.0.13"
end
   config.vm.define "fotamst" do |vagrant5|
    vagrant5.vm.box = "centos/7"
    vagrant5.vm.hostname = "fotamst"
    config.vm.synced_folder "/home/gagan/", "/fota", disabled: false
    vagrant5.vm.network "private_network", ip: "10.0.0.14"
end

end
