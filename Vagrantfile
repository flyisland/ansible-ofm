# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
  config.vm.box = "centos65-x86_64"

  config.vm.define "em12c" , primary: true do |em12c|
    em12c.vm.hostname = "em12c.example.com"
    em12c.vm.synced_folder "E:/OFM", "/software"
    em12c.vm.synced_folder "R:/", "/ramdisk"

    em12c.vm.network :private_network, ip: "10.10.10.10"

    em12c.vm.provider :virtualbox do |vb|
      vb.memory = 12288
      vb.cpus = 2
      vb.name = "em12c"
      file_to_disk = "S:/VirtualBoxVMs/disk/80g.vdi"
      unless File.exist?(file_to_disk)
        vb.customize ['createhd', '--filename', file_to_disk, '--size', 80 * 1024]
      end
      vb.customize ['storageattach', :id, '--storagectl', 'SATA', '--port', 1, '--device', 0, '--type', 'hdd', '--medium', file_to_disk]
    end

  end

end
