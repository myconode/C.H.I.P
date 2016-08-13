Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty32"
  config.vm.synced_folder "../data", "/vagrant_data"
    config.vm.synced_folder ".", "/home/vagrant/CHIP-SDK", disabled:true

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "1024"

    # Virtual I/O
    vb.customize ['modifyvm', :id, '--usb', 'on']
    vb.customize ['modifyvm', :id, '--usbehci', 'on']
    vb.customize ['usbfilter', 'add', '0', '--target', :id, '--name', 'CHIP',                              '--vendorid', '0x1F3A']
    vb.customize ['usbfilter', 'add', '0', '--target', :id, '--name', 'CHIP in fastboot mode',             '--vendorid', '0x18d1', '--product', '0x1010']
    vb.customize ['usbfilter', 'add', '0', '--target', :id, '--name', 'CHIP Linux Gadget USB Serial Port', '--vendorid', '0x0525', '--product', '0xA4A7']
    vb.customize ['usbfilter', 'add', '0', '--target', :id, '--name', 'PL2303 Serial Port',                '--vendorid', '0x067b', '--product', '0x2303']
  end

  config.vm.provision "shell", inline: <<-SHELL
    echo "install software"
  SHELL
end
