# -*- mode: ruby -*-
# vi: set ft=ruby :

# 设置环境变量
ENV["LC_ALL"] = "en_US.UTF-8"

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
  config.vm.box = "centos/7"

  config.vm.hostname = "centos-7"

  # ssh 登录用户, 从官方下载的box往往使用的是这个用户名。如果是自定制的box，所使用的用户名可能会有所不同，通过这个配置设定所用的用户名。
  config.ssh.username = "vagrant"

  # Box 版本号
  config.vm.box_version = ">= 0"

  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # NOTE: This will enable public access to the opened port
  # config.vm.network "forwarded_port", guest: 80, host: 8080

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine and only allow access
  # via 127.0.0.1 to disable public access
  # config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  config.vm.network "private_network", ip: "192.168.10.10"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../data", "/vagrant_data"

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  config.vm.provider "virtualbox" do |vb|
    # 设置虚拟机名称
    vb.name = "Centos-7";

    # # 是否打开GUI界面
    # vb.gui = true
   
    # Customize the amount of memory on the VM:
    vb.memory = "2048"

    # 设置CPU个数
    vb.cpus = 1
  end

  
  # Configure A Few Hyper-V Settings
  config.vm.provider "hyperv" do |vb|
    # 设置虚拟机名称
    vb.vmname = "Centos-7";

    # # 是否打开GUI界面
    # vb.gui = true
   
    # Customize the amount of memory on the VM:
    vb.memory = "2048"

    # 设置CPU个数
    vb.cpus = 2
  end
  
  # View the documentation for the provider you are using for more
  # information on available options.

  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  config.vm.provision "shell", inline: <<-SHELL
    # 安装宝塔程序
    yum install -y wget && wget -O install.sh http://download.bt.cn/install/install_6.0.sh && yes | bash install.sh

    # 安装Composer
    wget https://dl.laravel-china.org/composer.phar -O /usr/local/bin/composer
    # 设置权限
    sudo chmod a+x /usr/local/bin/composer
    
  #   apt-get update
  #   apt-get install -y apache2
  SHELL
end
