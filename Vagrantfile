Vagrant.configure("2") do |config|
  config.vm.box = "precise64"
  config.vm.box_url = "http://files.vagrantup.com/precise64.box"

  config.vm.network :private_network, ip: "192.168.50.4"  
  config.ssh.forward_agent = true
    
    # Set the Timezone to something useful
  config.vm.provision :shell, :inline => "echo \"America/Chicago\" | sudo tee /etc/timezone && dpkg-reconfigure --frontend noninteractive tzdata"  
	config.vm.provision :shell, :inline => "apt-get update --fix-missing"
  
  config.vm.synced_folder "./www", "/var/www", id: "vagrant-root"
  
   
  config.vm.provision :puppet do |puppet|
    puppet.manifests_path = "manifests"
    puppet.module_path = "modules"
    puppet.options = ['--verbose']
  end
  
end
