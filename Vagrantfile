Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"
  config.vagrant.plugins = ["vagrant-vbguest"]

  config.vm.provider "virtualbox" do |v|
    v.memory = 1024
    v.cpus = 2
  end

# vagrant-vbguest config options from
# https://github.com/dotless-de/vagrant-vbguest#config-options
  Vagrant::Config.run do |config|
    # we will try to autodetect this path. 
    # However, if we cannot or you have a special one you may pass it like:
    # config.vbguest.iso_path = "#{ENV['HOME']}/Downloads/VBoxGuestAdditions.iso"
    # or an URL:
    # config.vbguest.iso_path = "http://company.server/VirtualBox/%{version}/VBoxGuestAdditions.iso"
    # or relative to the Vagrantfile:
    # config.vbguest.iso_path = "../relative/path/to/VBoxGuestAdditions.iso"
    
    # set auto_update to false, if you do NOT want to check the correct 
    # additions version when booting this machine
    #config.vbguest.auto_update = false
    
    # do NOT download the iso file from a webserver
    #config.vbguest.no_remote = true
  end 

end    
