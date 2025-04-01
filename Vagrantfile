hosts = {
  "any" => "192.168.56.2"
}

Vagrant.configure("2") do |config|
    config.vm.box = "ubuntu/focal64"
    config.vm.box_url = "https://cloud-images.ubuntu.com/focal/current/focal-server-cloudimg-amd64-vagrant.box"
  hosts.each do |name, ip|
    config.vm.define name do |mashine|
      #mashine.vm.network :private_network, ip: ip
      mashine.vm.provider "virtualbox" do |vb|
        vb.name = "anynamevm"
	    vb.gui = false
	    vb.cpus = 2
	    vb.memory = "4096"
      end
    end
	
    config.vm.hostname = "anyhostname"
    config.vm.synced_folder "./tovm", "/vagrant"
    config.vm.network "forwarded_port", guest:3000, host:3000
	config.vm.network "forwarded_port", guest:9090, host:9090
	config.vm.network "forwarded_port", guest:9100, host:9100
    config.vm.provision "shell", path: "firstStartScript"
  end
end