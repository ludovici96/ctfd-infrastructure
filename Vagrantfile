# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  # Define the Redis VM
  config.vm.define "redis" do |redis|
    redis.vm.box = "ubuntu/focal64"
    redis.vm.network "private_network", ip: "192.168.56.10"
    redis.vm.provision "ansible" do |ansible|
      ansible.compatibility_mode = "2.0"
      ansible.playbook = "ansible/playbook.yml"
      ansible.inventory_path = "ansible/inventory/staging.yml"
      ansible.limit = 'redis'
    end
  end

  # Define the Database VM
  config.vm.define "db" do |db|
    db.vm.box = "ubuntu/focal64"
    db.vm.network "private_network", ip: "192.168.56.11"
    db.vm.provision "ansible" do |ansible|
      ansible.compatibility_mode = "2.0"
      ansible.playbook = "ansible/playbook.yml"
      ansible.inventory_path = "ansible/inventory/staging.yml"
      ansible.limit = 'db'
    end
  end

  # Define the CTFd VM
  config.vm.define "ctfd" do |ctfd|
    ctfd.vm.box = "ubuntu/focal64"
    ctfd.vm.network "private_network", ip: "192.168.56.12"
    #for testing ctfd
    #ctfd.vm.network "forwarded_port", guest: 8000, host: 8000
    ctfd.vm.provision "ansible" do |ansible|
      ansible.compatibility_mode = "2.0"
      ansible.playbook = "ansible/playbook.yml"
      ansible.inventory_path = "ansible/inventory/staging.yml"
      ansible.limit = 'ctfd'
    end
  end

  # Define the Nginx VM
  config.vm.define "nginx" do |nginx|
    nginx.vm.box = "ubuntu/focal64"
    nginx.vm.network "private_network", ip: "192.168.56.13"
    nginx.vm.network "forwarded_port", guest: 80, host: 80  # Forward host port 80 to guest port 80
    nginx.vm.provision "ansible" do |ansible|
      ansible.compatibility_mode = "2.0"
      ansible.playbook = "ansible/playbook.yml"
      ansible.inventory_path = "ansible/inventory/staging.yml"
      ansible.limit = 'nginx'
    end
  end
end
