Vagrant.configure("2") do |config|
  config.vm.provider "virtualbox"
  config.vm.box = "centos/7"
  config.vagrant.plugins = ["vagrant-vbguest"]

  # fine for dev boxes but use a private subnet for modelling real envs
  config.vm.network "private_network", type: "dhcp"

  # optimization tips on nfs from 
  # https://blog.theodo.com/2017/07/speed-vagrant-synced-folders/
  config.vm.synced_folder ".", "/vagrant", type: "nfs", nfs_export: true,
    mount_options: ['rw', 'vers=3', 'tcp'],
    linux__nfs_options: ['rw','no_subtree_check','all_squash','async']

  # Salt provisioner expects these to mapped to /srv/ on guest
  config.vm.synced_folder "./salt/", "/srv/", type: "nfs", nfs_export: true,
    mount_options: ['rw', 'vers=3', 'tcp'],
    linux__nfs_options: ['rw','no_subtree_check','all_squash','async']

  config.vm.provider "virtualbox" do |v|
    v.name = "mw-gm"
    v.memory = 2046
    v.cpus = 2
    # faster vm on private network using host DNS
    # https://serverfault.com/a/595010
    v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    v.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
  end

  ########### Provisioning ###########

  config.vm.provision :salt do |salt|
    salt.masterless = true
    salt.run_highstate = true
    salt.verbose = true
  end

end    
