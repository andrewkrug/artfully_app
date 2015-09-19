# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box      = "artfully_so"
  config.vm.box_url     = "https://s3-us-west-2.amazonaws.com/artfully-so/package.box"
  config.vm.network   "forwarded_port", guest: 3000, host: 3000
  config.vm.network   "forwarded_port", guest: 8983, host: 8983
  config.vm.synced_folder ".", "/vagrant/workspace"


  config.vm.provider "virtualbox" do |vb|
    vb.customize ["modifyvm", :id, "--memory", "4096"]
    vb.customize ["modifyvm", :id, "--cpus", "2"]
    # following configs resolve a bug causing bundle gem to hang 5 seconds per get
    vb.customize ["modifyvm", :id, "--natdnsproxy1", "off"]
    vb.customize ["modifyvm", :id, "--natdnshostresolver1", "off"]
  end
end


#Kicking the tires on this box quickly.

#Clone the repo
#vagrant up
#vagrant ssh
#cd workspace ( this is the shared folder )
#bundle
#cp config/database.yml.sample config/database.yml
#rake db:create:all
#rake db:schema:load
#In the rails console User.create!({:email => "youradmin@example.com", :password => "your_strong_password", :password_confirmation => "your_strong_password" })

#Note there is also an installation of solr on this base box on port 8983 and an smtp server on localhost for testing those functions when we figure it out.

