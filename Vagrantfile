Vagrant.configure("2") do |config|
  config.vm.box = 'ubuntu/jammy64'
  # config.vm.provider "vmware_desktop" do |v|
    # v.gui = true
  # end
  config.vm.provider "virtualbox" do |v|
	v.memory = 3072
  end
  config.vm.define "uba" do |host|	
    host.vm.network "private_network" , ip: "192.168.1.197", virtualbox__intnet: true
	#host.vm.network "public_network", bridge: "en0: Wi-Fi (Wireless)"
	host.vm.hostname = "uba"
	host.vm.provision "file", source: "./99_config.yaml", destination: "/tmp/99_config.yaml"	
	host.vm.provision "shell", inline: "mv /tmp/99_config.yaml /etc/netplan/99_config.yaml; \
	netplan apply"
	host.vm.provision "file", source: "C:/Users/dns/Desktop/peacock/docker-compose.yml", destination: "~/docker-compose.yml"
	host.vm.provision "shell", inline: "apt-get update; \
	curl -fsSL https://get.docker.com -o install-docker.sh; \
	sh install-docker.sh;\
	sudo docker compose up -d
	"
  end
  
  config.vm.define "ubb" do |host|
    host.vm.network "private_network", ip: "192.168.1.198", virtualbox__intnet: true
	#host.vm.network "public_network", bridge: "en0: Wi-Fi (Wireless)"
	host.vm.hostname = "ubb"
	host.vm.provision "shell", inline: "sleep 2; apt-get update; \
	snap install cqlsh
	"
  end

end
