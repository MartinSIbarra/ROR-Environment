# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://vagrantcloud.com/search.
  config.vm.box = "debian/jessie64"

  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # NOTE: This will enable public access to the opened port
  # config.vm.network "forwarded_port", guest: 80, host: 8080
  # config.vm.network "forwarded_port", guest: 5000, host: 5000

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine and only allow access
  # via 127.0.0.1 to disable public access
  # config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  # config.vm.network "private_network", ip: "192.168.33.10"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../data", "/vagrant_data"
  # config.vm.synced_folder "D:/workspace/rails", "/home/vagrant/workspace",
  #   mount_options: ["dmode=775,fmode=664"]


  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  config.vm.provider "virtualbox" do |vb|
    vb.name = "ROR-Environment"
  #   # Display the VirtualBox GUI when booting the machine
  #   vb.gui = true
  #
    # Customize the amount of memory on the VM:
    vb.memory = "2048"
  end
  #
  # View the documentation for the provider you are using for more
  # information on available options.

  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  config.vm.provision "shell", inline: $script_env, privileged: true
  config.vm.provision "shell", inline: $script_ruby, privileged: false
  config.vm.provision "shell", inline: $script_terminal, privileged: false
end

$script_env = <<-SHELL
  # Virtualbox guest addons
  sudo echo 'deb http://httpredir.debian.org/debian jessie contrib' >> /etc/apt/sources.list
  sudo apt-get update
  # sudo apt-get install virtualbox-guest-dkms virtualbox-guest-utils -y

  # PostgreSQL
  sudo apt-get install postgresql postgresql-client postgresql-contrib postgresql-server-dev-all -y

  sudo sed -i'' 's/local\s*all\s*postgres\s*peer/local all postgres trust/' /etc/postgresql/9.4/main/pg_hba.conf

  sudo /etc/init.d/postgresql restart

  # Redis
  sudo apt-get install redis-server -y

  # Tools
  sudo apt-get install zip curl git wget lynx silversearcher-ag bc gem nodejs vim vim-common vim-doc -y
SHELL

$script_ruby = <<-SHELL
  # RUBY ON RAILS installation
  # rvm installation
  curl -sSL https://rvm.io/mpapis.asc | gpg2 --import -
  curl -sSL https://get.rvm.io | bash -s stable
  source /home/vagrant/.rvm/scripts/rvm

  # ruby installation
  rvm install 2.3.4

  # rails installation
  gem install rails

  # bundler installation
  rvm all do gem install bundler

  # setting ruby
  rvm --default use 2.3.4
SHELL

$script_terminal = <<-SHELL
  curl -sSL https://raw.githubusercontent.com/MartinSIbarra/terminalrc/master/bin/shell_init_script.sh | bash
SHELL
