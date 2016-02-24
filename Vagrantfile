# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.configure(2) do |config|
  rubyversion = File.read('rubyversion')
  config.vm.box = "puppetlabs/centos-7.2-64-nocm"
  config.vm.provision 'shell', inline: 'rpm --import /etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7'
  config.vm.provision 'shell', inline: 'yum makecache'
  config.vm.provision "shell", inline: 'yum install -y deltarpm'
  config.vm.provision "shell", inline: 'yum groupinstall -y "Development Tools"'
  config.vm.provision "shell", inline: "yum install -y centos-release-scl scl-utils"
  config.vm.provision 'shell', inline: 'yum install -y gcc bzip2 openssl-devel libyaml-devel libffi-devel readline-devel zlib-devel gdbm-devel ncurses-devel git'
  config.vm.provision 'shell', inline: 'git clone https://github.com/rbenv/rbenv.git /opt/rbenv'
  config.vm.provision 'shell', inline: 'echo \'export PATH="/opt/rbenv/bin:$PATH"\' >> /etc/profile.d/rbenv.sh'
  config.vm.provision 'shell', inline: 'echo \'eval "$(rbenv init -)"\' >> /etc/profile.d/rbenv.sh'
  config.vm.provision 'shell', inline: 'echo "export RBENV_ROOT=/opt/rbenv" >> /etc/profile.d/rbenv.sh'
  config.vm.provision 'shell', inline: 'chown -R vagrant /opt/rbenv/'
  config.vm.provision 'shell', inline: 'type rbenv'
  config.vm.provision 'shell', inline: 'git clone https://github.com/rbenv/ruby-build.git /opt/rbenv/plugins/ruby-build'
  config.vm.provision 'shell', inline: "rbenv install #{rubyversion}"
  config.vm.provision 'shell', inline: "rbenv global #{rubyversion}"
end
