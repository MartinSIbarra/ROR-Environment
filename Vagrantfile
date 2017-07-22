$script_ruby = <<-SHELL
  RUBY_VERSION="2.2.3"
  # Install ruby environment
  if ! type rvm >/dev/null 2>&1; then
    curl -sSL https://rvm.io/mpapis.asc | gpg --import -
    curl -L https://get.rvm.io | bash -s stable
    source /home/vagrant/.rvm/scripts/rvm
  fi

  if ! rvm list rubies ruby | grep ruby-${RUBY_VERSION}; then
    rvm install ${RUBY_VERSION}
  fi

  rvm all do gem install bundler
  rvm --default use ${RUBY_VERSION}
SHELL

$script_system = <<-SHELL
  # Virtualbox guest addons
  sudo echo 'deb http://httpredir.debian.org/debian jessie contrib' >> /etc/apt/sources.list
  sudo apt-get update
  sudo apt-get install virtualbox-guest-dkms virtualbox-guest-utils -y

  # PostgreSQL
  sudo apt-get install postgresql postgresql-client postgresql-contrib postgresql-server-dev-all -y

  sudo sed -i'' 's/local\s*all\s*postgres\s*peer/local all postgres trust/' /etc/postgresql/9.4/main/pg_hba.conf

  sudo /etc/init.d/postgresql restart

  # Redis
  sudo apt-get install redis-server -y

  # Tools
  sudo apt-get install zip curl git -y

SHELL

$script_git = <<-SHELL
  ssh-keyscan github.com >> ~/.ssh/known_hosts
  chmod 600 ~/.ssh/id_*
  chmod 644 ~/.ssh/id_*.pub

  rvm use 2.2.3
SHELL

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://atlas.hashicorp.com/search.
  config.vm.box = "debian/jessie64"

  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
   config.vm.network "forwarded_port", guest: 5000, host: 5000

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  # config.vm.network "private_network", ip: "192.168.33.10"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
   config.vm.network "public_network"


  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  # config.vm.provision "shell", inline: <<-SHELL
  #   sudo apt-get update
  #   sudo apt-get install -y apache2
  # SHELL
  config.vm.provision "shell", inline: $script_system, privileged: true
  config.vm.provision "shell", inline: $script_ruby, privileged: false
  config.vm.provision "shell", inline: $script_git, privileged: false

  #config.vm.provision "shell", inline: $script_mount, privileged: true

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.

  # Uncomment this to have access to the repo from outside the VM
  config.vm.synced_folder "D:/workspace", "/home/vagrant/workspace",
    mount_options: ["dmode=775,fmode=664"]


  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  config.vm.provider "virtualbox" do |vb|
    vb.name = 'RubyDevelopment'
    # Display the VirtualBox GUI when booting the machine
    #vb.gui = true

    # Customize the amount of memory on the VM:
    #vb.memory = "3072"
  end
  #
  # View the documentation for the provider you are using for more
  # information on available options.

  # Define a Vagrant Push strategy for pushing to Atlas. Other push strategies
  # such as FTP and Heroku are also available. See the documentation at
  # https://docs.vagrantup.com/v2/push/atlas.html for more information.
  # config.push.define "atlas" do |push|
  #   push.app = "YOUR_ATLAS_USERNAME/YOUR_APPLICATION_NAME"
  # end


end
