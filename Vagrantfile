# -*- mode: ruby -*-
# vi: set ft=ruby :


Vagrant.configure("2") do |config|
  config.vm.box = "Debian7"
  config.vm.box_url = "https://dl.dropboxusercontent.com/u/8506456/debian-7.4_c64.box"
  config.vm.network "private_network", ip: "192.168.33.104"


  config.vm.provision "chef_solo" do |chef|
    chef.cookbooks_path = "site-cookbooks/"
    chef.run_list = %w[
      recipe[apt::default]
      recipe[nginx]
      recipe[vim]
      recipe[mysql::client]
    ]
  end

  config.omnibus.chef_version = :latest
  config.berkshelf.enabled = true


end
