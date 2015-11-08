Vagrant.configure(2) do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.
  
  config.vm.box = "boxcutter/ubuntu1404" # using the boxcutter box as it works across vmware, parallels and virtualbox.

  config.vm.network "public_network"
  config.vm.network "forwarded_port", guest: 27017, host: 27017
  
  # Enable provisioning with a shell script.
  config.vm.provision "shell", privileged: false, inline: <<-SHELL
    echo "Making sure OS is properly updated"
    sudo apt-get update
    sudo apt-get -y upgrade
    sudo apt-get update
    echo "Installing Nodejs"
    sudo apt-get install -y curl
    curl -sL https://deb.nodesource.com/setup_4.x | sudo -E bash -
    sudo apt-get update
    sudo apt-get -y install nodejs
    sudo apt-get -y install build-essential libssl-dev git git-core
    echo "Upgrading Npm"
    sudo npm update -g npm  
    echo "Installing MongoDb"
    sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 7F0CEB10
    echo "deb http://repo.mongodb.org/apt/ubuntu trusty/mongodb-org/3.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.0.list
    sudo apt-get update
    sudo apt-get install -y mongodb-org
    echo "You can access the mongodb by using the mongodb://localhost:27017 endpoint in your MongoDb management tool (or you can use the"
    echo "'mongo' command from a shell on your vagrant box."
    echo ""
  SHELL
end

