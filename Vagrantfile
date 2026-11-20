IMAGE_NAME = "bento/debian-13"

HOST_NAME = "spos-debian13-moskalova"

Vagrant.configure("2") do |config|
    config.ssh.insert_key = false

    config.vm.provider "virtualbox" do |v|
        v.memory = 1024
        v.cpus = 1
    end

    config.vm.define "debian" do |debian|
        debian.vm.box = IMAGE_NAME
        debian.vm.hostname = HOST_NAME

        debian.vm.network "forwarded_port",
            guest: 22, host: 2206, host_ip: "127.0.0.1"

        debian.vm.network "forwarded_port",
            guest: 80, host: 8080, host_ip: "127.0.0.1"

        debian.vm.provision "shell", path: "install-zabbix-agent2.sh"
    	debian.vm.provision "shell", path: "configure-zabbix-agent2.sh"
    end
end
