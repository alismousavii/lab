Vagrant.configure("2") do |config|
  (1..2).each do |i|
    config.vm.define "ubuntuhost-#{i}" do |machine|
      machine.vm.box = 'ubuntu/jammy64'
      machine.vm.hostname = "ubuntuhost-#{i}"
      machine.vm.network "private_network", ip: "192.168.56.12#{i}"
      machine.vm.provider "virtualbox" do |vb|
        vb.name = "ubuntu-#{Time.now.to_i}-#{i}"
	      vb.cpus = 1
        vb.memory = 512
      end
      machine.vm.provision "shell", inline: <<-SHELL
        apt update -y
        apt install -y python3 python3-pip
      SHELL
    end
  end
end
