Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"

  config.vm.network "private_network", ip: "10.11.12.27"

  config.vm.provider "virtualbox" do |vb|
    #vb.name = "ubox_#{Time.now.to_i}"
    vb.name = "ubox"
    vb.memory = "1024"
  end

  #config.vm.provision "shell", inline: IO.read('bin/setup')
end
