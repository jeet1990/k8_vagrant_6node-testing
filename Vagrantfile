Vagrant.configure("2") do |config|
    config.vm.provision "shell", inline: <<-SHELL
        apt-get update -y
        echo "10.10.10.93  ha-node" >> /etc/hosts
        echo "10.10.10.90  master-node90" >> /etc/hosts
        echo "10.10.10.91  master-node91" >> /etc/hosts
        echo "10.10.10.92  master-node92" >> /etc/hosts   
        echo "10.10.10.100  worker-node100" >> /etc/hosts
        echo "10.10.10.101  worker-node101" >> /etc/hosts
        echo "10.10.10.102  worker-node102" >> /etc/hosts
    SHELL
    

    config.vm.define "ha-node" do |master|
      master.vm.box = "bento/ubuntu-18.04"
      master.vm.hostname = "ha-node"
      master.vm.network "private_network", ip: "10.10.10.93"
      master.vm.provider "virtualbox" do |vb|
          vb.memory = 4048
          vb.cpus = 2
      end
      # master.vm.provision "shell", path: "scripts/common.sh"
      # master.vm.provision "shell", path: "scripts/master.sh"
    end


    (0..2).each do |i|

    config.vm.define "master-node9#{i}" do |master|
      master.vm.box = "bento/ubuntu-18.04"
      master.vm.hostname = "master-node9#{i}"
      master.vm.network "private_network", ip: "10.10.10.9#{i}"
      master.vm.provider "virtualbox" do |vb|
          vb.memory = 4048
          vb.cpus = 2
      end
      # master.vm.provision "shell", path: "scripts/common.sh"
      # master.vm.provision "shell", path: "scripts/master.sh"
    end
    
  end
    (0..2).each do |i|
  
    config.vm.define "worker-node10#{i}" do |node|
      node.vm.box = "bento/ubuntu-18.04"
      node.vm.hostname = "worker-node10#{i}"
      node.vm.network "private_network", ip: "10.10.10.10#{i}"
      node.vm.provider "virtualbox" do |vb|
          vb.memory = 4096
          vb.cpus = 2
      end
      # node.vm.provision "shell", path: "scripts/common.sh"
      # node.vm.provision "shell", path: "scripts/node.sh"
    end
    
  end
end