Vagrant.configure(2) do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.
  
  config.vm.box = "boxcutter/ubuntu1404" # using the boxcutter box as it works across vmware, parallels and virtualbox.

  config.vm.network "public_network"
  config.vm.network "forwarded_port", guest: 5000, host: 5000


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
    sudo apt-get -y install build-essential libssl-dev
    echo "Upgrading Npm and installing the Yoman Generator"
    sudo npm update -g npm  
    sudo npm install -g yo  
    sudo npm install -g generator-aspnet  
    echo "Organising Zsh and your working environment"
    git clone https://github.com/robbyrussell/oh-my-zsh.git ~/.oh-my-zsh
    cp ~/.oh-my-zsh/templates/zshrc.zsh-template ~/.zshrc
    sudo chsh -s /bin/zsh vagrant
    curl https://raw.githubusercontent.com/shabbirh/VagrantVnext/master/zshrc.default > ~/.zshrc
    sudo apt-get -y install software-properties-common python-software-properties
    sudo add-apt-repository ppa:djcj/screenfetch
    sudo apt-get update
    sudo apt-get -y install fortune
    sudo apt-get -y install screenfetch
    sudo apt-get -y install htop
    echo "Installing MongoDb"
    sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 7F0CEB10
    echo "deb http://repo.mongodb.org/apt/ubuntu trusty/mongodb-org/3.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.0.list
    sudo apt-get update
    sudo apt-get install -y mongodb-org
    echo "Installing mongodb-express (via npm globally)"
    echo "Installing PM2"
    echo "Starting mongodb-express with PM2"
    echo "You can access the administration Url by going to http://localhost:5000"
  SHELL
end

