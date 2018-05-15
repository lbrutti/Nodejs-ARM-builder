Vagrant::Config.run do |config|
  config.vm.box = "ubuntu/bionic64"
  config.vm.box_url = "https://app.vagrantup.com/ubuntu/boxes/bionic64"

  config.vm.share_folder("cross-compiler", "/home/vagrant/cross-compiler", ".")

  # Allow symlinks
  config.vm.customize ["setextradata", :id, "VBoxInternal2/SharedFoldersEnableSymlinksCreate/cross-compiler", "1"]
  # Otherwise the compile will go into swap, making things slow
  config.vm.customize ["modifyvm", :id, "--memory", 2048]
  # Setup virtual machine
  config.vm.provision :shell, :inline => "./cross-compiler/cross-compiler.sh"
end
