Vagrant.configure(2) do |config|
  config.vm.host_name = "trusty"

  config.vm.box_url = "https://cloud-images.ubuntu.com/vagrant/trusty/current/trusty-server-cloudimg-amd64-vagrant-disk1.box"
  config.vm.box = "trusty64"

  config.vm.network :private_network, ip: "192.168.33.10"
  config.vm.network :forwarded_port, host: 27017, guest: 27017
  config.vm.network :forwarded_port, host: 28017, guest: 28017

  config.vm.provision "docker" do |d|
    d.pull_images 'dockerfile/mongodb'
    d.run 'dockerfile/mongodb',
      name: 'mongodb',
      args: "-p 27017:27017"
  end
end
