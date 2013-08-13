# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant::Config.run do |config|

  # Every Vagrant virtual environment requires a box to build off of.
  # config.vm.box = "centos63"
  # config.vm.box_url = "/Users/sean/veewee-centos63/centos63.box"
  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "centos63"
  config.vm.box_url = "https://dl.dropbox.com/sh/9rldlpj3cmdtntc/56JW-DSK35/centos-62-32bit-puppet.box"

  config.vbguest.auto_update = true
  config.vbguest.auto_reboot = true

  # config.vm.box = "centos-6.4-64"
  # config.vm.box_url = "http://developer.nrel.gov/downloads/vagrant-boxes/CentOS-6.4-x86_64-v20130309.box"
  # Boot with a GUI so you can see the screen. (Default is headless)
  #config.vm.boot_mode = :gui

  # Assign this VM to a host-only network IP, allowing you to access it
  # via the IP. Host-only networks can talk to the host machine as well as
  # any other machines on the same network, but cannot be accessed (through this
  # network interface) by any external networks.
  config.vm.network :hostonly, "192.168.56.60"

  config.vm.host_name = "pydev.local"

  # Assign this VM to a bridged network, allowing you to connect directly to a
  # network using the host's network device. This makes the VM appear as another
  # physical device on your network.
  # config.vm.network :bridged

  # Forward a port from the guest to the host, which allows for outside
  # computers to access the VM, whereas host only networking does not.
  config.vm.forward_port 80, 8080
  config.vm.forward_port 5000, 8081

  # Share an additional folder to the guest VM. The first argument is
  # an identifier, the second is the path on the guest to mount the
  # folder, and the third is the path on the host to the actual folder.
  #config.vm.share_folder "v-projects", "/projects", "./projects"

  config.vm.provision :puppet,
    :options => ["--fileserverconfig=fileserver.conf"],
    :facter => { "fqdn" => "vagrant.vagrantup.com" }  do |puppet|
       puppet.manifests_path = "manifests"
       puppet.manifest_file = "init.pp"
  end

end
