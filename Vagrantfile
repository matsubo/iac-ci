# -*- mode: ruby -*-
# vi: set ft=ruby :


Vagrant.configure("2") do |config|
  config.vm.box = "Debian7"
  config.vm.box_url = "https://dl.dropboxusercontent.com/u/8506456/debian-7.4_c64.box"
  config.vm.network "private_network", ip: "192.168.33.104"


  # test without chef
#  config.vm.provision "chef_solo" do |chef|
#    chef.cookbooks_path = "site-cookbooks/"
#    chef.run_list = %w[
#      recipe[apt::default]
#      recipe[nginx]
#      recipe[ntp]
#    ]
#    #recipe[vim]
#    #recipe[mysql::client]
#  end


  config.vm.provider :digital_ocean do |provider, override|
    override.ssh.private_key_path = '~/.ssh/id_rsa'
    override.vm.box               = 'digital_ocean'
    override.vm.box_url           = "https://github.com/smdahlen/vagrant-digitalocean/raw/master/box/digital_ocean.box"
    provider.private_networking   = true
    provider.token                = ENV["DIGITALOCEAN_TOKEN"]
    provider.image                = 'Debian 7.0 x64'
    provider.region               = 'nyc3'
    provider.size                 = '256mb'


    if ENV['WERCKER'] == "true"
      provider.ssh_key_name         = 'wercker'
    else
      provider.ssh_key_name         = 'metaps mac'
    end
  end



  # test without chef
#  config.omnibus.chef_version = :latest
#  config.berkshelf.enabled = true


end
