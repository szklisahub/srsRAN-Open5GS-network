Vagrant.configure("2") do |config|
  config.vm.box = "generic/ubuntu2204"
  config.vm.synced_folder "C:/Users/lisas/NetworkPjt", "/usr/network"
  #config.vm.provision "shell", run: "always", inline: "systemctl restart network.service"

  # VM1
  config.vm.define :cplane do |cp|
    cp.vm.hostname = "cplane"
    cp.vm.disk :disk, size: "20GB", primary: true

    cp.vm.provider "virtualbox" do |vb|
      vb.name = "5GC C-Plane"
      vb.memory = "1024"
      vb.cpus = 1
      # preventing the timeout after "default: SSH auth method: private key" -> effectively solved the issue
      vb.customize ["modifyvm", :id, "--cableconnected1", "on"]
    end

    cp.vm.network "private_network", ip: "192.168.1.111", netmask: "24", auto_config: false
    cp.vm.network "forwarded_port", guest: 9999, host: 9999   # HTTP open5gs-webui
    # config.vm.network "private_network", ip: "3001::1", netmask: "64"
  end

  # VM2
  config.vm.define :uplane do |up|
    up.vm.hostname = "uplane"
    up.vm.disk :disk, size: "20GB", primary: true

    up.vm.provider "virtualbox" do |vb|
      vb.name = "5GC U-Plane"
      vb.memory = "1024"
      vb.cpus = 1
      # preventing the timeout after "default: SSH auth method: private key" -> effectively solved the issue
      vb.customize ["modifyvm", :id, "--cableconnected1", "on"]
    end

    up.vm.network "private_network", ip: "192.168.1.112", netmask: "24", auto_config: false
    # config.vm.network "private_network", ip: "3001::1", netmask: "64"
  end

  # VM3
  config.vm.define :gnb do |gnb|
    gnb.vm.hostname = "gnb"
    gnb.vm.disk :disk, size: "10GB", primary: true

    gnb.vm.provider "virtualbox" do |vb|
      vb.name = "gNodeB"
      vb.memory = "4096"
      vb.cpus = 2
      # preventing the timeout after "default: SSH auth method: private key" -> effectively solved the issue
      vb.customize ["modifyvm", :id, "--cableconnected1", "on"]
    end

    gnb.vm.network "private_network", ip: "192.168.1.121", netmask: "24", auto_config: false
    # config.vm.network "private_network", ip: "3001::1", netmask: "64"
  end

  # VM4
  config.vm.define :ue do |ue|
    ue.vm.hostname = "ue"
    ue.vm.disk :disk, size: "10GB", primary: true

    ue.vm.provider "virtualbox" do |vb|
      vb.name = "UE"
      vb.memory = "4096" # 2048 was not enough...
      vb.cpus = 2
      # preventing the timeout after "default: SSH auth method: private key" -> effectively solved the issue
      vb.customize ["modifyvm", :id, "--cableconnected1", "on"]
    end

    ue.vm.network "private_network", ip: "192.168.1.122", netmask: "24", auto_config: false
    # config.vm.network "private_network", ip: "3001::1", netmask: "64"
  end
end
