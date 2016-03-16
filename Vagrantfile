VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "ubuntu/trusty64"

  config.vm.network :private_network, ip:    "192.168.33.100"
  config.vm.network "forwarded_port", guest: 80, host: 8080

  config.vm.synced_folder ".",  "/vagrant", id: "vagrant-root", :nfs => true
  config.vm.synced_folder "..", "/var/www", id: "application",  :nfs => true

  config.vm.provider "virtualbox" do |v|
    v.memory = 1024
    v.cpus = 2
  end

  config.vm.provision :ansible do |ansible|
    ansible.playbook = "playbook.yml"
  end
end
